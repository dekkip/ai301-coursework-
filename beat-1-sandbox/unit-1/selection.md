# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73

**Verdict output**

```
Repo-level facts gathered (push date today, no releases). Now fetching each issue's details.

  Ran 3 shell commands

All three issues pass the required checks. One caveat: scope.md's fit profile section is still unfilled ("Write a few sentences here"), and all three tie on every preferred check too — so I can't produce a genuine fit-based ranking. I'm listing them in a reasonable default order (by estimated effort, smallest first) but flagging that this isn't a rubric-driven rank.

Repo-level facts (apply to all three): last push today (2026-09-16T21:48Z), no releases ever published, repo not archived.

#73 — README/.env.example disagree on LLM API key (accept)
- Community alive: pass — push today
- Repo in use: pass — last push within 6mo (no releases, but rubric accepts either signal)
- Scope fits you: pass — no OS field mentioned
- Issue unclaimed: pass — no assignees, no linked/mentioned PRs
- Notably tiny scope (1–2h, two files), labeled good first issue/docs

#64 — Relevance scorer test fixture has full overlap, not partial (accept)
- Same repo-level checks: pass/pass/pass/pass
- Small, self-contained (one test fixture), no linked PRs, good first issue/tests

#69 — Output parser crashes on top-level JSON array (accept)
- Same repo-level checks: pass/pass/pass/pass
- Slightly larger (2–4h, touches an xfail test marker too), good first issue/rag

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73",
    "checks": [
      {"name": "Community alive", "grade": "pass", "evidence": "Repo last push 2026-09-16T21:48:27Z, same day as grading — within 30 days"},
      {"name": "Repo in use", "grade": "pass", "evidence": "No releases exist, but last push 2026-09-16 is within 6 months"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Issue body has no 'Operating system' field at all"},
      {"name": "Issue is unclaimed", "grade": "pass", "evidence": "assignees: [] and no PRs in repo reference or link issue #73"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/64",
    "checks": [
      {"name": "Community alive", "grade": "pass", "evidence": "Repo last push 2026-09-16T21:48:27Z — within 30 days"},
      {"name": "Repo in use", "grade": "pass", "evidence": "No releases exist, but last push 2026-09-16 is within 6 months"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Issue body has no 'Operating system' field at all"},
      {"name": "Issue is unclaimed", "grade": "pass", "evidence": "assignees: [] and no PRs in repo reference or link issue #64"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69",
    "checks": [
      {"name": "Community alive", "grade": "pass", "evidence": "Repo last push 2026-09-16T21:48:27Z — within 30 days"},
      {"name": "Repo in use", "grade": "pass", "evidence": "No releases exist, but last push 2026-09-16 is within 6 months"},
      {"name": "Scope fits you", "grade": "pass", "evidence": "Issue body has no 'Operating system' field at all"},
      {"name": "Issue is unclaimed", "grade": "pass", "evidence": "assignees: [] and no PRs in repo reference or link issue #69"}
    ],
    "verdict": "accept"
  }
]
```

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

1. First full run (rubric used a "Scope fits you" check based on the repo's primary language, which is not a field present in the eval bundles): `agreement: 13/20 scored items  (bar: 18/20: below the bar)`, with `categories: claimed 4/4  clear-accept 2/8  dead-repo 3/3  policy 1/1  scope 3/4`.
2. Final full run (after rewriting "Scope fits you" to check the issue body's "Operating system" field instead, and moving it to `preferred`): `agreement: 18/20 scored items  (bar: 18/20: PASS)`, with `categories: claimed 4/4  clear-accept 7/8  dead-repo 3/3  policy 1/1  scope 3/4`. This is the run saved to `eval-run.txt`.

**Issue analysis**

`issue-09` — gold label: `accept`. My rubric's verdict: `reject`, failed on `Issue is unclaimed`. That check requires the bundle's assignees field to be empty and its linked-PRs field to show no linked PRs; it fired because the bundle recorded an assignee or a linked PR against the issue, and since the check is `required`, any fail there rejects the issue outright. The gold label disagreeing suggests the assignee or PR the bundle recorded was likely stale, inactive, or abandoned rather than active ownership — a distinction between "someone is on this" and "someone was on this once" that my check's evidence (bare presence/absence) has no way to represent.

**Check rationale**

Quoted as written in `rubric.md`:

| Issue is unclaimed | Assignees field, linked PRs field | No assignees, and no linked PRs | required |

I made this `required`, not `preferred`, because an issue someone is already working means my time on it is largely wasted even if every other signal about the repo is good — it's the one check where a fail should override everything else, so it belongs in the "required" tier rather than just nudging the ranking.

**Trade-offs**

This same "Issue is unclaimed" check gives up any notion of a *stale* claim. It treats an assignee or a linked PR as disqualifying regardless of how old or inactive it is, which is exactly what produced the miss on `issue-09` above (gold: accept, mine: reject). I'm accepting that trade-off for now: telling a stale assignment from a live one would need an evidence source these bundles don't reliably carry (e.g., days since the assignee's last activity on the issue), and I'd rather keep a simple, predictable required check than build a fragile heuristic on evidence that may not exist for every issue.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. I'm working full-time while taking this course, so I wanted the smallest real win rather than the most interesting one. #73 is a two-file mismatch between the README and `.env.example` over an API key name, estimated at 1-2 hours — that fits the time I actually have this week.
2. The verdict correctly confirmed the repo is genuinely active (a push the same day I ran the skill) and that the issue is truly unclaimed (no assignee, no linked PR). What it couldn't weigh, because my fit profile was still blank when I ran it, is that all three accepted candidates tied on every check — I picked #73 over #64 and #69 myself, based on it touching the fewest files and having the least ambiguous reproduction steps.
3. I expect claiming it to be straightforward: the fix is likely a one-line correction to make the README and `.env.example` agree on the key name, so the main work before I write the Unit 2 claim comment is just confirming which of the two is the authoritative name.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
