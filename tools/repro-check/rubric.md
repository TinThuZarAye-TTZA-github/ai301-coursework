# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check              | Evidence                                                                                                                            | Pass condition                                                                                                                                                                                                                                                                                                                                                      | Weight   |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| environment        | Repro report's environment record                                                                                                   | Pass if the report identifies the software version and relevent system/environment information needed for another person to understand the conditions of the reproduction.                                                                                                                                                                                          | required |
| reproduction-steps | Repro report's commands, inputs, and setup steps                                                                                    | Pass if the commands., inputs, and setup information are complete enough for another person to follow and attampt the same reproduction                                                                                                                                                                                                                             | required |
| behavior-match     | Repro reports's observed output or artificat read against the behavior described in the original issue                              | Pass if the evidenced demostrates the same behavior described by the issue. A different or adjancent eror does not pass                                                                                                                                                                                                                                             | required |
| honest-outcome     | Repro report's states outcome read aganist its commands, outputs and artifacts                                                      | Pass if the stated conclusion accurately matches the evidence shown. An honestly evidenced connot-reproduce result passes; claiming successful reproduction when the evidence show different behavior fails.                                                                                                                                                        | required |
| repo-conventions   | Claims comment and repro report read aganist the repository's contribution guidelines, templates, and stated AI/disclosure policies | Pass if the comments follow the repository's stated contribution requirements. If the repository requires AI-use disclosure, the claim comment or repro report must include the required disclosure, including the tool and extent of assistance when the policy asks for them. If required disclosure is missing, fail. If no relevant convention is stated, pass. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accepts if every required check passes. Reject if any required check fail. An unclear result on a required check counts as fail.
