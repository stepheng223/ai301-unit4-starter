# Unit 4: Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-howard/pull/91

Opened from `stepheng223/pathreview-ai301-fa26-howard:fix/64-partial-overlap-fixture` against `codepath/pathreview-ai301-fa26-howard:main`. Fix commit: `bddfee49e798607880d35a5eb4d28da94a2f8125`. Published diff verified: one file, one insertion, five deletions, exactly matching plan.md. The GitHub description names issue #64, fills the template, and includes before/after repro output, check evidence, limitations and Codex disclosure.

Issue: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64
Posted plan: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/64#issuecomment-6138056972

**Branch**

`fix/64-partial-overlap-fixture`

## Eval iterations

**Run history**

1. Initial full invocation inside the restricted sandbox: all 20 Claude calls exited with errors, no packages were graded (0/0), and the harness refused to save eval-run.txt. This was an execution failure, not an agreement score.
2. Confirming full run with Claude login/network access, unchanged tool: 18/20 scored items, PASS. Categories: clear-accept 5/7; not-tested 4/4; silent-drift 4/4; standards-wall 2/2; unreviewable 3/3. This is the harness-written eval-run.txt submitted here. No partial or calibration runs were used. The full per-check results are in eval-results.json.

**Package analysis**

pkg-11: my tool returned reject; the gold label is accept. The deciding plan-fidelity evidence was: "Description claims tests for 'the escaped, unescaped, and double-backslash cases', but the diff's test covers only the escaped (foo\   ) and double-backslash (foo\\   ) cases; no unescaped-trim test exists."

The rubric requires description claims to match actual delivered evidence. The grader treated the description's test-coverage claim as an unsupported promise, even though the escaped-space repro, focused parser change and cargo suite were supported. The gold accepts this package; my check over-rejects a secondary test-description discrepancy. I retained the check because catching unsupported claims is useful, while acknowledging this false rejection. I do not claim the gold label is wrong.

**Check rationale**

The exact current row from tools/pr-precheck/rubric.md is:

> | plan-fidelity | Plan-context scope, implementation steps and deviations compared with every diff hunk and candidate description. | Every behavioral change and omitted planned outcome is accounted for by the plan or explicit deviation notes, and the description accurately states what the diff delivers. An honestly disclosed limitation or deferred edge is allowed; silent expansion, omission, or contradictory fidelity claims fail. | required |

I wrote this to compare both directions: extra unplanned changes and silently omitted promised work. I rejected a strict “all original plan steps must ship” rule because a recorded deviation or disclosed deferred edge can be honest and reviewable. The description/diff comparison remains strict, which explains pkg-11's false rejection. No rubric revisions followed the confirming run; the saved fingerprints describe the uploaded files.

**Trade-offs**

This tool prefers a hold when claim fidelity is uncertain. It over-rejected pkg-11 and pkg-16, both gold accept. For pkg-16, the grader could not verify the start-path tolerance claim from the shown caller and rejected a bare go-test success claim without captured output. Those are real costs of demanding observable evidence from a frozen bundle. I did not loosen checks after reaching the bar: the full run demonstrates that the unchanged tool catches both standards-wall packages and every not-tested, silent-drift and unreviewable package. Future loosening should re-run these disagreements plus canaries in the affected small categories before another full confirmation.

## Applied evidence and limits

The carried-over plan is plan.md, including its Deviations section. build-evidence-before.txt and build-evidence-after.txt are original Unit 3 captures, not new runs. fix.diff contains exactly the planned fixture replacement and removal of its strict xfail. repository-checks.txt contains fresh local check attempts and outcomes. pr-description.md is the reviewable publication draft. The local live precheck and current limitations are recorded in live-precheck.txt.

Fresh validation: lint, black and mypy passed; CI-equivalent unit suite passed 376 tests with 52 other seeded xfails; frontend passed 18 tests. Integration collected no tests, the condition explicitly permitted by the CI shim. The pre-publication live precheck returned reject while publication and CI were unavailable; it is preserved in live-precheck-before-publication.txt. The PR is now published and all five GitHub CI jobs passed. The final live precheck is accept; see live-precheck.txt and github-status.json.

## Final live precheck

**Verdict: accept.** All five required rubric checks pass. The issue #64 fixture and strict xfail edits match the plan exactly; original repro and fresh after outputs demonstrate the change; local checks and all five GitHub CI jobs pass; the diff contains no unrelated work; the published description fills every template section and discloses Codex assistance. No voice-rule violations were found. The integration job passes through the repository's documented empty-suite shim, so this does not claim integration test coverage.

PR: https://github.com/codepath/pathreview-ai301-fa26-howard/pull/91
CI evidence: https://github.com/codepath/pathreview-ai301-fa26-howard/actions/runs/39710395339

Precheck history: the pre-publication run was reject for unavailable publication/CI evidence; after pushing the fork branch, opening PR #91 and verifying all five jobs, the final run is accept. The tool files did not change, so the saved 18/20 eval and its fingerprints remain current.
