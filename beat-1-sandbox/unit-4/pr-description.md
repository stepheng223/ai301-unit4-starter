## Summary
Correct the partial-overlap test fixture: its old chunk contained every query token and correctly scored 1.0. The replacement omits Django, shares three of four tokens, and scores 0.75. The scorer implementation is unchanged.

## Issue
Closes #64

Plan: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6138056972
Reproduction: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6090767203

## Changes
- Replace only the chunk in `test_query_with_partial_overlap`.
- Remove that test's strict xfail marker. No matching pyproject suppression exists for issue #64.
- Keep the query, assertion band and scorer unchanged. No plan deviations.

## Testing
- [x] **CI is green on this PR (all five jobs)** — lint, typecheck, test-unit, test-integration and frontend all passed: https://github.com/codepath/pathreview-ai301-fa26-howard/actions/runs/39710395339
- [x] Unit tests pass: CI-equivalent `LLM_PROVIDER=mock .venv/bin/python -m pytest tests/unit -v --tb=short`: **376 passed, 52 xfailed**, exit 0. The 52 remaining xfails belong to other seeded issues.
- [x] Integration CI passes (empty-suite shim): `make test-integration` exits 2 because pytest collects no tests (pytest exit 5). The current CI workflow explicitly treats this empty-suite result as success; no integration coverage is claimed.
- [x] Linter passes: `make lint`, exit 0.
- [x] Type checker passes: `make typecheck`, 76 source files, exit 0.
- [x] New/updated tests cover the changes: all 19 relevance-scorer tests pass; targeted partial-overlap test passes.
- [x] Seeded bug's strict xfail removed; no matching suppression to remove.

Also: `black --check .` leaves all 110 files unchanged; frontend `npm test -- --run` passes 18 tests across 2 files.

Before (original Unit 3 capture at base 99673c7):
```text
$ .venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
18 passed, 1 xfailed
$ .venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
E assert 1.0 < 0.9
1 failed, 18 deselected
```

After (fresh local verification of this exact diff on macOS / Python 3.12.3):
```text
$ .venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q -rxX
19 passed
$ .venv/bin/python -m pytest tests/unit/test_relevance_scorer.py -q --runxfail -k partial_overlap
1 passed, 18 deselected
```

Direct calls to the real scorer in the Unit 3 capture returned 1.0 for the original chunk and 0.75 for the replacement. Expected-after is a genuinely partial overlap within the existing 0.3–0.9 band, with perfect-match and zero-overlap controls retained.

## Screenshots / Demo
Not applicable: this change only corrects a Python test fixture. The command outputs above demonstrate the behavior.

## Notes for Reviewers
Only `tests/unit/test_relevance_scorer.py` changes, with one insertion and five deletions. The initial broad local run was blocked by missing dependencies, and the next by a tokenizer-data download restriction. After installing the declared dependencies and allowing that download, the CI-equivalent unit run passed. Local Python 3.12 validation does not establish the outcome of GitHub's Python 3.11 jobs. All five GitHub CI jobs passed for commit bddfee4; the integration job uses the documented empty-suite shim.

AI assistance: OpenAI Codex helped draft the plan and PR text, make the bounded fixture edit, and execute and interpret validation. The recorded commands and outputs are actual runs.
