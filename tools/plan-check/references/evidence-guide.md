# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

Where it lives:

- In an eval package, read the candidate plan's diagnosis together with the repro-evidence block, issue context, and relevant thread highlights.
- In live mode, read the diagnosis in the draft plan against the student's reproduction comment and the relevant issue-thread discussion.

What good looks like:
The stated cause explains behavior that the reproduction evidence actually demonstrates and does not contradict observations from the reproduction. A diagnosis based only on a claim in the issue thread is not enough when the reproduced behavior points to a different cause.

## Scope

Where it lives:

- In an eval package, read the candidate plan's scope statement, proposed changes, and named files or components.
- In live mode, inspect the draft plan's in-scope and not-in-scope statements and compare them with the reproduced issue.

What good looks like:
The proposed work is bounded to the behavior demonstrated by the reproduction and names the files or areas that need to change. Unrelated cleanup, broad rewrites, or changes that are not necessary to address the reproduced problem indicate scope creep.

## Executability

Where it lives:

- In an eval package, read the candidate plan's proposed files, changes, implementation approach, risks, and unknowns.
- In live mode, inspect the draft plan and relevant repository structure or documentation needed to understand the proposed work.

What good looks like:
Another contributor can identify where to begin and what behavior to change without having to guess at the core implementation approach. The plan should distinguish evidence-supported decisions from assumptions or unresolved questions.

## Test plan

Where it lives:

- In an eval package, read the candidate plan's test plan against the commands, steps, observations, and expected behavior in the repro-evidence block.
- In live mode, compare the draft test plan with the student's posted reproduction steps and any relevant existing tests in the repository.

What good looks like:
The test plan exercises the behavior that originally reproduced the problem and states an observable expected result after the change. It should be capable of distinguishing the broken behavior from the fixed behavior and should include relevant regression checks when the proposed change could affect related behavior.

## Honesty

Where it lives:

- In an eval package, inspect the candidate plan's risks, unknowns, assumptions, and deviations when present, and compare confident claims with the available evidence.
- In live mode, inspect the draft plan's risks and unknowns and, during implementation, the Deviations section.

What good looks like:
Known uncertainties are stated as uncertainties rather than presented as established facts. If implementation differs materially from the posted plan, the deviation is recorded and the plan is updated rather than silently changing direction.

## Comms

Where it lives:

- In an eval package, read the candidate plan comment against the issue context, thread highlights, repo-facts block, contribution instructions, and any stated AI-use disclosure policy.
- In live mode, read the draft comment against the current GitHub issue thread and the repository's contributing documentation, issue or PR templates, and contribution policies.

What good looks like:
The comment accurately represents the student's own diagnosis, scope, and test approach and responds to relevant maintainer or contributor context in the thread. It follows applicable repository requirements, including disclosure requirements when one exists, without inventing requirements that the repository does not state.
