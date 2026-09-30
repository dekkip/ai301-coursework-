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

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The repro report's Environment section | Pass if the tool version and OS are concrete, named values (e.g. "yq 4.53.3, macOS 15.5"), not vague ("latest version") or missing | required |
| steps-runnable | The repro report's Preparation and Execution sections | Pass if a stranger could re-run the steps and observe the specific reported behavior without guessing any detail that affects whether the bug reproduces. An unstated detail with no bearing on the bug (e.g. arbitrary package names in an otherwise-valid dependency list) does not fail this check | required |
| behavior-matches-issue | The repro report's Actual section, compared against the issue's stated actual behavior | Applies only when the report claims a reproduction occurred. Pass if the failure shown is the same failure the issue reports (same error type, message, or crash signature). An honest "could not reproduce" report is graded under outcome-honesty instead, not here | required |
| outcome-honesty | The repro report's stated conclusion, compared against what its own Preparation/Execution/Actual sections show | Pass if the conclusion is supported by the report's own evidence. An honest "could not reproduce," backed by what was tried, is a pass. A claimed reproduction the shown output doesn't support is a fail | required |
| claim-no-overpromise | The candidate claim comment's language about what happens next | Pass if the claim promises only investigation/reproduction and a report. Fail if it promises a fix, a resolution, or a specific completion date/timeframe | required |
| conventions-respected | The repo-facts block's contribution/AI policy, compared against the literal text of the claim comment and repro comment | Pass if the repo states no policy requiring disclosure of AI assistance in issues/comments, OR the repo states such a policy and the comment includes an explicit disclosure naming the tool and the extent of assistance. Fail if the repo's stated policy requires disclosure and the comment contains no disclosure statement at all | required |

## Verdict rule

Accept (ready) only if every required check passes. `unclear` counts as a fail for any required check. There are no preferred checks in this rubric — every family the lecture named is load-bearing for whether a bad package should go up, so none of them just rank; all of them can hold.
