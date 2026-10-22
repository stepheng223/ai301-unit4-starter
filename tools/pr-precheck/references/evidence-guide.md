# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

Eval: pair plan-context scope, exclusions, steps and deviation notes with candidate unified diff and description. Live: use plan.md including Deviations, the upstream-default three-dot branch diff, commits and draft PR text. Every hunk and omitted planned outcome must have an explanation within the plan or its recorded deviations. A disclosed shortfall can be ready; a description claiming work absent from the diff cannot.

## Test evidence (harness category: not-tested)

Eval: read plan-context reproduction and test plan, repo-facts check requirements, and candidate test-evidence outputs and description. Live: read the reproduction record and captured before/after commands and outputs, CI/check results and repository check configuration. Good evidence names input, command, observed behavior and expected result; verify the test exercises the reported failure. Separately locate outcomes for repository checks. A documented unrelated blocker with relevant validation can be acceptable; a green unrelated suite or an unsupported “tests pass” cannot replace behavioral proof.

## Diff quality (harness category: unreviewable)

Eval: inspect candidate unified diff and commits against the plan. Live: inspect the complete branch diff and commit list relative to the upstream default branch. The fix and its supporting changes should be inspectable without unrelated hunks, debug prints, commented-out code or generated artifacts drowning them out. Judge the contents, not line count; explain why a suspicious hunk is unrelated before failing it.

## Standards and comms (harness category: standards-wall)

Eval: read repo-facts PR-template asks and contribution/AI policies verbatim, then maintainer directions in thread highlights; match them against candidate title and description. Live: read the actual .github PR template, CONTRIBUTING.md and linked contribution/AI policy and issue thread, then draft PR text. Required sections need real answers, including an explicit not-applicable explanation where appropriate. A required disclosure must identify tool and extent if requested; consider assistance mentioned in thread lineage, not just the candidate's claims. Do not invent universal requirements when repo facts state none. Description/diff contradictions belong to plan fidelity. Personal voice guidance applies only in live mode and is reported separately.
