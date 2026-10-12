# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

1. Determine whether the review is in live mode or eval mode.

2. In live mode, read `scope.md` first. Verify that the target
   repository is allowed. Read `voice-guide.md` for the PR writing
   requirements. In eval mode, ignore both files.

3. Read `rubric.md` to identify every check, its pass condition,
   its weight, and the verdict rule.

4. Read `references/evidence-guide.md` to identify where each
   type of evidence is located.

5. Read the related issue and `plan.md`, including its scope,
   implementation steps, test plan, and documented deviations.
   Record the intended changes and boundaries before inspecting
   the implementation.

6. Read the committed code diff. In live mode, run
   `git diff main...HEAD` from the Path Review repository root.
   Record every changed file and the behavior it changes.

7. Read `test_evidence.md` and compare the reported results
   against the plan's test steps and the repository's required
   checks.

8. Read the proposed PR title and description from `pr_draft.md`.
   Compare the claims against the actual diff and test evidence.

9. Read the repository's PR template and contribution requirements.
   In eval mode, use only the repository facts supplied in the
   practice package.

10. Do not assign grades until the relevant evidence has been
    collected. Reading the plan before the diff prevents the
    implementation from redefining its own intended scope.
<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

## Evidence gathering

1. Plan fidelity:
   Compare each changed file and behavior in the committed diff
   against the issue, plan.md, and documented deviations.
   Record any changes that were added, omitted, or modified
   without explanation.

2. Test evidence:
   Compare the test plan with test_evidence.md and the PR's
   testing claims. Record the commands executed, observable
   results, failures, and missing checks.
   Distinguish honestly disclosed limitations from unsupported
   claims of successful testing.

3. Diff quality:
   Inspect changed files and hunks for unrelated changes,
   debug statements, commented-out code, accidental files,
   and unnecessary modifications. Record specific examples.

4. Standards and communication:
   Compare the PR title and description with the repository's
   PR template, contribution requirements, and actual diff.
   Check required sections, issue references, AI-use disclosure,
   and accuracy of implementation and testing claims.

5. For every check, record the exact evidence supporting
   the decision. If evidence is missing, record what is
   unavailable rather than assuming it passed.

6. In eval mode, gather all evidence exclusively from the
   supplied practice package. Do not access external sources.


<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

## Check execution

1. Execute every check in rubric.md in the order listed:
   Plan fidelity, Test evidence, Diff quality, and
   Standards and communication.

2. For each check, use the evidence gathered in the
   previous stage and apply its exact pass condition.

3. Assign one grade:
   - pass: The evidence satisfies the pass condition.
   - fail: The evidence contradicts the pass condition.
   - unclear: Necessary evidence is missing or cannot
     establish whether the condition passed.

4. Record one specific evidence line for each grade.
   Reference the relevant file, diff, test output,
   or statement from the PR package.

5. Do not invent evidence or assume that a missing
   test passed. Apply the rubric's treatment of
   honestly disclosed limitations.

6. Reuse previously gathered evidence when sufficient.
   Re-read a source only when needed to resolve a
   specific uncertainty.

7. Complete all checks even when an earlier required
   check fails. Do not change the rubric or grading
   criteria during the review.
<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Verdict assembly

1. Collect the grades for all four rubric checks:
   Plan fidelity, Test evidence, Diff quality, and
   Standards and communication.

2. Apply the rubric's verdict rule:
   - accept: Every required check is graded pass.
   - reject: At least one required check is graded
     fail or unclear.

3. Treat unclear as failing for the final verdict.
   Do not convert unclear to pass without evidence.

4. If the verdict is reject, identify the first
   required check graded fail or unclear in rubric
   order. Use that check as the deciding reason.

5. Write a concise human-readable summary explaining
   the verdict, the deciding evidence, and any other
   important failures or uncertainties.

6. Include every rubric check in the JSON output,
   with its name, grade, and one-line evidence.

7. End the response with exactly one fenced JSON
   object using the schema in CONTRACT.md:

   {
     "item": "<PR URL or bundle id>",
     "checks": [
       {
         "name": "<check name>",
         "grade": "pass|fail|unclear",
         "evidence": "<one-line supporting fact>"
       }
     ],
     "verdict": "accept|reject"
   }

8. Do not add text after the JSON block.
   Do not change the schema or omit any checks.

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->
