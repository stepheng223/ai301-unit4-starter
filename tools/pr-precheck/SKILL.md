---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading



## The question

Decide whether one candidate PR is ready to submit. Read its title, description, commits, diff and test evidence against its issue and accepted plan, including recorded deviations.



## Inputs and modes

In live mode read the issue and thread, repository PR template and contribution/AI policies, plan.md with deviations, branch diff from `git diff main...HEAD` (use the actual upstream default branch if different), commits, draft title/description, and captured test outputs. House-chain students use the house plan and repro pack. In eval mode use only the supplied bundle: fetch nothing and read no other artifacts. Run every check and the full verdict rule.



## The scope seam (live mode only)

Before any other live read, read scope.md. If Repo is a placeholder, stop without grading and ask for the section Path Review repository. Refuse to grade a different target repository. Enforce the listed house rules. Eval mode ignores scope.md entirely.



## The voice seam (live mode only)

Read voice-guide.md in live mode and compare the outgoing title and description to each rule. Report broken rules in the summary; voice alone never changes the verdict because the rubric has no personal-voice check. Ignore this file in eval mode.



## Component reads

Read rubric.md for checks and the verdict rule, references/evidence-guide.md for evidence sources, then execute procedure.md as written. Refuse to grade an empty or comment-only rubric or procedure. Report procedural gaps rather than inventing steps; mark unverifiable required evidence unclear.



## Verdict and output

Emit accept for ready to submit or reject for hold. Provide a brief evidence summary if useful. End with the following fenced JSON schema, populated with every check in rubric order. Preserve key order; add no keys and nothing after the fence.



```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Cite a concrete fact or quote for every grade. Judge the artifact, not polish or length. Apply the written pass conditions even when intuition differs; changes belong in the rubric, never improvised in a run. Follow the procedure and report gaps. Unclear required evidence prevents acceptance. Honest disclosed limitations may pass under the explicit rules; never invent proof or requirements.


