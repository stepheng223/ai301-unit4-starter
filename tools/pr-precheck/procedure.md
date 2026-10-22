# Procedure: how this tool grades a PR package

## Read order

1. Resolve mode. In live mode enforce scope first, then read voice. In eval mode read only the bundle.
2. Read the rubric and evidence guide. Read the issue, thread and repo facts; record the requested behavior, template asks, policy obligations and required checks.
3. Read the plan before the candidate description. Record scope, excluded changes, implementation steps, test plan and deviations so the candidate cannot silently redefine its promises.
4. Read candidate title, description, commits, every diff hunk and test evidence. Record claims separately from observed proof.

## Evidence gathering

1. Plan fidelity: map each changed hunk and each planned outcome to the plan or a deviation note. Compare description claims with actual changes in both directions. Record disclosed limitations separately from silent omissions.
2. Test evidence: pair the reproduction inputs and expected behavior with before/after commands and outputs. Record what each check actually exercises, missing observations, and any explicit cannot-reproduce outcome. Inventory repo checks against actual outcomes and stated blockers; distinguish related failures from unrelated known failures.
3. Diff quality: inspect all hunks and commits for unrelated changes, churn and debug or generated debris. Record exact paths and examples; a filename alone does not prove irrelevance.
4. Standards: inventory every template ask, contribution requirement, AI-disclosure obligation and applicable maintainer direction. Match each to candidate content, noting empty boilerplate and any assistance evidenced by the thread. In live mode also record voice violations separately.

## Check execution

Execute checks in table order using the paired evidence. For each, apply only its written pass condition and record pass, fail or unclear with a one-line decisive quote or fact and its section/path. Missing mandatory proof is fail; ambiguous evidence is unclear. Do not infer execution from a description's confidence. Do not fail merely because a limitation is honestly recorded when the pass condition permits it. Revisit a source only if a contradiction requires resolving it. Grade every check even after a failure. Report a procedure gap without inventing a new rule.

## Verdict assembly

Apply the rubric's verdict rule: required fail or unclear yields reject; otherwise accept. In the readable summary quote the first failing required check in rubric order (or first unclear required check if none fail), and state the concrete repair needed. For accept identify the evidence supporting readiness and retain material limits. End with the contract JSON containing every check in order, item URL or bundle id, and binary verdict; nothing follows it.
