# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the issue and thread highlights first. Record the reported problem, expected behavior, relevant maintainer comments, and any constraints already established in the discussion.
2. Read the reproduction evidence next. Record the exact behavior reproduced, the commands or steps used, the observed results, and what those results support about the cause of the problem.
3. Read the repo facts and contribution requirements. Record any relevant repository conventions, templates, or disclosure requirements.
4. Read the candidate plan after the evidence. Record its diagnosis, proposed scope, files to change, implementation approach, test plan, risks, and unknowns.
5. Read the candidate plan comment last. Compare what it claims with the detailed plan, reproduction evidence, issue thread, and repository conventions.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. For diagnosis, compare the plan's stated cause with the reproduction evidence and relevant issue or thread evidence. Record evidence that supports or contradicts the stated cause.
2. For root-cause-target, compare the proposed changes with the supported diagnosis. Record whether the change acts on the demonstrated cause or only on an unrelated or downstream symptom.
3. For bounded-scope, record the files and behavior the plan proposes changing, what it explicitly leaves out, and whether any proposed work is unrelated to the reproduced issue.
4. For executable-plan, record the proposed files, implementation steps, assumptions, risks, and unknowns. Identify whether another contributor could begin the work from this information without depending on unsupported assumptions.
5. For test-plan, compare the proposed test steps and expected results with the original reproduction. Record what observable behavior each test would verify and whether the tests would demonstrate that the reproduced problem is fixed without hiding regressions.
6. For thread-conventions, compare the plan comment with the issue thread, repo facts, contribution requirements, and any stated disclosure policy. Record any relevant requirement that the comment follows or violates.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade diagnosis first. Pass only when the stated cause is supported by the available reproduction and issue evidence and does not contradict it.
2. Grade root-cause-target next using the supported diagnosis. Pass only when the proposed change addresses that cause rather than an unrelated or downstream symptom.
3. Grade bounded-scope by checking that the proposed work stays focused on the reproduced issue and does not introduce unnecessary changes.
4. Grade executable-plan by deciding whether the gathered implementation information gives another contributor enough evidence-supported direction to begin the work.
5. Grade test-plan by checking whether its tests exercise the relevant behavior and have observable expected results that can show whether the problem is fixed without hiding regressions.
6. Grade thread-conventions by checking the plan comment against relevant thread context and repository contribution or disclosure requirements.
7. Mark a check unclear when the package contains relevant evidence but it is insufficient or ambiguous enough that the pass condition cannot be determined. Do not guess or fill missing evidence with assumptions.
8. Mark a check fail when the available evidence directly violates its pass condition or required evidence is absent in a way that prevents the condition from being satisfied.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Collect the grade for every rubric check before deciding the final verdict.
2. Apply the rubric verdict rule exactly: accept only if every required check passes.
3. Treat any failed required check as reject.
4. Treat any unclear required check as fail and therefore reject.
5. In the output, identify each check's grade and briefly cite the package evidence that determined it, especially the evidence for any check that caused a reject verdict.
6. Return the final binary verdict as accept for a ready plan or reject for a plan that should be held.
