# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

dekkip

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73#issuecomment-5901778691 

Hi! I'd like to take on issue #73 (the README and `.env.example` disagree on the LLM API key name) as my first contribution here. I'll investigate
which of the two has the correct key name, and I'll post a reproduction report on this issue with what I find. Thank you!

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73#issuecomment-5902005846 

Hi again — I need to correct my last comment, since my check missed
something.

I only grepped the codebase for the literal uppercase strings
OPENAI_API_KEY and OPENROUTER_API_KEY, which found OPENAI_API_KEY in
ingestion/embeddings/provider.py but no match for OPENROUTER_API_KEY.
From that alone, I concluded .env.example was correct and the
README's OPENROUTER_API_KEY reference was stale.

That conclusion was wrong. I hadn't opened core/config.py, which
defines the app's Settings class (a pydantic_settings.BaseSettings
subclass). It explicitly includes:

    openai_api_key: str = Field(default="")
    openrouter_api_key: str = Field(default="")
    openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
    openrouter_model: str = Field(default="google/gemma-3-27b-it:free")

Pydantic Settings maps these field names to environment variables
case-insensitively, so OPENROUTER_API_KEY is a real, supported
variable the app reads — my literal-string grep just couldn't see it,
since the code never spells the name in uppercase.

So the mismatch runs the other way from what I said before:
.env.example is the incomplete file. Its LLM_PROVIDER comment lists
only "mock" and "openai", and it has no OPENROUTER_API_KEY,
OPENROUTER_BASE_URL, or OPENROUTER_MODEL entries, even though
core/config.py supports all three. The README's Quick Start
instruction to set OPENROUTER_API_KEY is accurate.

Sorry for the confusion in my last comment — thank you for your
patience while I got this right.


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

First full run — agreement: 15/20 scored items (bar: 18/20: below the bar; category floor unmet: no match in disclosure), with categories: clear-accept 5/8 disclosure 0/1 no-evidence 4/4 unfollowable-comms 2/3 wrong-target 4/4.
Second full run (after reworking steps-runnable and behavior-matches-issue, and adding claim-no-overpromise) — agreement: 19/20 scored items (bar: 18/20: below the bar; category floor unmet: no match in disclosure), with categories: clear-accept 8/8 disclosure 0/1 no-evidence 4/4 unfollowable-comms 3/3 wrong-target 4/4.
Partial canary check (--only pkg-20,pkg-05,pkg-09, after rewording conventions-respected) — agreement: 3/3 scored items, with categories: clear-accept 2/2 disclosure 1/1 — confirmed the reworded disclosure check without flipping the two packages it previously got right.
Final confirming full run — agreement: 18/20 scored items (bar: 18/20: PASS), with categories: clear-accept 6/8 disclosure 1/1 no-evidence 4/4 unfollowable-comms 3/3 wrong-target 4/4. This is the run saved to eval-run.txt.

**Package analysis**

pkg-20 — gold label: reject. My rubric's verdict: reject (correct, after revision). The repo (ghostty-org/ghostty) states a strict policy: "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance." Neither the candidate's claim comment nor its repro report contains any disclosure statement. My conventions-respected check originally read this package as accept anyway, because its pass condition only checked whether comments "met" the policy without forcing an explicit comparison — a comment with no visible violation looked like it passed by default. I reworded the check to explicitly fail when a repo's stated policy requires disclosure and the comment contains none, which correctly flipped this package to reject.

**Check rationale**

Quoted as currently written in rubric.md:

| conventions-respected | The repo-facts block's contribution/AI policy, compared against the literal text of the claim comment and repro comment | Pass if the repo states no policy requiring disclosure of AI assistance in issues/comments, OR the repo states such a policy and the comment includes an explicit disclosure naming the tool and the extent of assistance. Fail if the repo's stated policy requires disclosure and the comment contains no disclosure statement at all | required |

I revised this from an earlier version that just said "pass if the comments meet any policy the repo states... passes by default if the policy states nothing relevant." That wording let the grader read "no obvious violation" as "meets policy," which missed a package with a strict, explicit AI-disclosure requirement and no disclosure present. The current wording forces a concrete yes/no comparison — is a disclosure statement present when one is required — rather than a vague judgment call.

**Trade-offs**

Tightening conventions-respected fixed the disclosure-category miss on pkg-20, but it introduced a new miss elsewhere: pkg-07 (gold: accept, my verdict: reject, failed conventions-respected). The stricter reading that correctly catches Ghostty's explicit "all AI usage must be disclosed" policy is apparently reading something in pkg-07's repo policy as requiring disclosure too strictly, when the gold label says it shouldn't reject. I'm accepting this trade-off for now: it's a single miss against a category floor that was previously unmet entirely, and the assignment's own bar (18/20 plus every category matched) is satisfied either way.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
