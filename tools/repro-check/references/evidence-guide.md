# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->
Where it lives: in an eval bundle, the repro report's **Environment** section (or equivalent opening block), plus the issue's own stated environment (version, OS, install method) and the repo-facts block's bug-report template fields, so you can compare the two. In live mode, this is the student's draft repro report and the original GitHub issue thread (its body, which usually states the version/OS the reporter used).

What good looks like: the report names a concrete tool version and OS (e.g. "yq 4.53.3, macOS 15.5 (arm64)"), not a category or a vague phrase ("latest", "my machine"). If the version tested differs from the version the issue targets, the report says so explicitly rather than silently substituting one for the other.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->
Where it lives: the repro report's **Preparation** and **Execution** sections (input file/data shown, exact command run). In live mode, the same sections of the student's draft.

What good looks like: someone with no prior context could copy the input and the command exactly as written and land in the same starting state the report describes, with zero values to fill in (no "run the build," no "set it up first" without saying how). The test is whether a stranger could execute it, not how many steps are listed or whether it follows a template's headings.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->
Where it lives: the repro report's **Actual** (or Analysis) section — the literal output, error text, panic trace, or screenshot produced by running the steps — read against the issue's own stated actual behavior (its error text or described symptom). In live mode, this is the draft report's output excerpt read against the GitHub issue body.

What good looks like: the failure shown is the *same* failure the issue reports — matching error type, message, or crash signature — not a different failure that happens to also be a failure. A parse error is not a panic, even if both are "fatal." If the artifact doesn't show the issue's specific behavior, this check fails regardless of how confident the report's prose sounds.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->
Where it lives: the gap between the repro report's stated conclusion (its Analysis/Expected/Actual wording, or an explicit "could not reproduce") and what its own Preparation/Execution/Actual sections actually demonstrate.

What good looks like: the conclusion follows from the evidence shown in the same report. A report that says "I could not reproduce this after N attempts" and shows those attempts is a pass — cannot-reproduce is an honest outcome, not a failure. A report that asserts reproduction ("this confirms the bug") when its own output doesn't match the issue's behavior, or is silent on the mismatch, is a fail — confidence does not substitute for support.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->
Where it lives: the repo-facts block's contribution policy (including any AI-use disclosure requirement), read against the actual text of the claim comment and the repro comment. In live mode, this is the repo's CONTRIBUTING.md / issue template (found on GitHub) read against the student's draft comment text.

What good looks like: the comments do whatever the repo's stated policy requires — most commonly, disclosing AI assistance if the policy asks for it — and speak to this specific issue (naming its number, its actual symptom) rather than reusable boilerplate that could be pasted onto any issue. If the repo states no relevant policy, this check passes by default; it never fails a package for a policy the repo never asked for.
