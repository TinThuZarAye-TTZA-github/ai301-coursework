# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check              | Evidence                                                                                                                 | Pass condition                                                                                                                                                            | Weight   |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| diagnosis          | The plan's stated cause read against the reproduction evidence and issue/thread evidence                                 | Pass if the proposed diagnosis is supported by the reproduced behavior and does not contradict the evidence.                                                              | required |
| root-cause-target  | The plan's proposed changes read against its diagnosis and the reproduction evidence                                     | Pass if the proposed change addresses the supported cause of the reproduced problem rather than only an unrelated or downstream symptom.                                  | required |
| bounded-scope      | The plan's scope, files to change, and proposed changes                                                                  | Pass if the work is a bounded change focused on the reproduced issue and avoids unrelated changes or unnecessary scope expansion.                                         | required |
| executable-plan    | The plan's proposed files, changes, approach, risks, and unknowns                                                        | Pass if the plan provides enough concrete, evidence-supported direction for another contributor to begin implementing it without relying on unsupported assumptions.      | required |
| test-plan          | The plan's test steps and expected results read against the reproduction evidence                                        | Pass if the tests exercise the relevant behavior and define observable results that would demonstrate whether the reproduced problem is fixed without hiding regressions. | required |
| thread-conventions | The plan comment read against the issue thread, repo facts, contribution requirements, and stated repository conventions | Pass if the comment is consistent with relevant thread context and follows applicable repository contribution and disclosure requirements.                                | required |

## Verdict rule

Accept if every required check passes. Reject if any required check fails. An unclear result on a required check counts as fail.
