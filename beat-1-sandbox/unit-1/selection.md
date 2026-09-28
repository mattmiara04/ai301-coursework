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

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
 Accepted (1)

  #53 — PII scrubber fails to redact parenthesized US phone numbers — the only candidate with a clear field. No assignee,
  and its timeline shows zero cross-referenced PRs; the six classmate claim comments are all author_association: NONE,
  which the Path Review house rule says to ignore. Fit: the body carries a runnable repro with observed-vs-expected
  output, names safety/pii_scrubber.py, and lists the four covering tests — exactly the "clear repro + specific files"
  shape you asked for, and it's a bounded Python regex fix with no architecture in the way.

  Rejected (2) — both sank on the same required check, Issue is available:

  - #68 — open PR #78 "fix: handle empty keyword indexes", body Closes #68, opened 2026-09-27. Every other required check
    passes.
  - #72 — open PR #75 "fix(security): fail closed in verify_password…", body Closes #72, opened 2026-09-26. Every other
    required check passes.

  The house rule waives claim comments, not open PRs — "everything else in the rubric applies as written" — so a real open
  PR implementing the issue still blocks. Worth noting the tension: course credit attaches to the PR you open, not to
  whether it merges, so the rule that makes shared issues cost nothing arguably extends to these too. That's a rubric
  edit, not a grading call, so I graded them as written.

  Shared evidence across all three: last non-bot default-branch commit 2026-09-16 (Andrew Burke), archived: false,
  pushed_at: 2026-09-16, and no AI ban in docs/CONTRIBUTING.md, the PR template, or any policy file — the repo's own
  commits carry Co-Authored-By: Claude.

  [
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53",
      "checks": [
        {"name": "Maintainer activity", "grade": "pass", "evidence": "Non-bot default-branch commit by Aburke225 (Andrew
  Burke) on 2026-09-16, 11 days before the 2026-09-27 capture date."},
        {"name": "Repository in use", "grade": "pass", "evidence": "Repo JSON: archived: false, disabled: false, pushed_at
  2026-09-16 (within 180 days)."},
        {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One bounded fix: phone regex in pii_scrubber.py,
  with repro snippet and four named failing tests; labels 'good first issue' and 'tier-1'; no umbrella, support question,
  design debate, or core-internals statement."},
        {"name": "Issue is available", "grade": "pass", "evidence": "assignee: null, assignees: []; timeline shows no
  cross-referenced or connected PR; all 12 claim comments are author_association NONE (classmates), which the Path Review
  house rule says do not block."},
        {"name": "AI-assisted contribution allowed", "grade": "pass", "evidence": "No AI ban in docs/CONTRIBUTING.md,
  .github/PULL_REQUEST_TEMPLATE.md, or any AI-policy file; repo's own commits carry 'Co-Authored-By: Claude Opus 5'."},
        {"name": "First-issue signal", "grade": "pass", "evidence": "Labels include 'good first issue' (Good for
  newcomers) and 'tier-1' (Starter difficulty)."}
      ],
      "verdict": "accept"
    },
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/68",
      "checks": [
        {"name": "Maintainer activity", "grade": "pass", "evidence": "Non-bot default-branch commit by Aburke225 (Andrew
  Burke) on 2026-09-16, 11 days before the 2026-09-27 capture date."},
        {"name": "Repository in use", "grade": "pass", "evidence": "Repo JSON: archived: false, disabled: false, pushed_at
  2026-09-16 (within 180 days)."},
        {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One bounded fix: empty-corpus guard in
  rag/retriever/keyword_search.py plus removing the H-01 xfail; estimated effort 2-4 hours; no umbrella, design debate, or
  core-internals statement."},
        {"name": "Issue is available", "grade": "fail", "evidence": "Open PR #78 'fix: handle empty keyword indexes' by
  Tiyatrotist, body 'Closes #68', created 2026-09-27, state open, not merged."},
        {"name": "AI-assisted contribution allowed", "grade": "pass", "evidence": "No AI ban in docs/CONTRIBUTING.md,
  .github/PULL_REQUEST_TEMPLATE.md, or any AI-policy file."},
        {"name": "First-issue signal", "grade": "pass", "evidence": "Labels include 'good first issue' (Good for
  newcomers) and 'tier-1' (Starter difficulty)."}
      ],
      "verdict": "reject"
    },
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72",
      "checks": [
        {"name": "Maintainer activity", "grade": "pass", "evidence": "Non-bot default-branch commit by Aburke225 (Andrew
  Burke) on 2026-09-16, 11 days before the 2026-09-27 capture date."},
        {"name": "Repository in use", "grade": "pass", "evidence": "Repo JSON: archived: false, disabled: false, pushed_at
  2026-09-16 (within 180 days)."},
        {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "One bounded fix: make verify_password in
  core/security.py fail closed plus remove the H-05 xfail; estimated effort 1-2 hours; no umbrella, design debate, or
  core-internals statement."},
        {"name": "Issue is available", "grade": "fail", "evidence": "Open PR #75 'fix(security): fail closed in
  verify_password on malformed stored hashes' by kragent66-glitch, body 'Closes #72', created 2026-09-26, state open, not
  merged."},
        {"name": "AI-assisted contribution allowed", "grade": "pass", "evidence": "No AI ban in docs/CONTRIBUTING.md,
  .github/PULL_REQUEST_TEMPLATE.md, or any AI-policy file."},
        {"name": "First-issue signal", "grade": "pass", "evidence": "Labels include 'good first issue' (Good for
  newcomers) and 'tier-1' (Starter difficulty)."}
      ],
      "verdict": "reject"
    }
  ]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

`agreement: 3/4 scored items`

`agreement: 4/4 scored items`

`agreement: 10/10 scored items`

`agreement: 18/20 scored items (bar: 18/20: PASS)`

My first partial run scored 3/4. After revising the Newcomer-sized scope check, the next partial run scored 4/4. I then tested 10 issues and scored 10/10. My final committed full run scored 18/20.

**Issue analysis**

`issue-19  accept  reject  NO  failed: Newcomer-sized scope, First-issue signal (preferred)`

My rubric rejected issue-19, while the gold label was accept. The required check that caused the rejection was Newcomer-sized scope. The First-issue signal also failed, but that check is preferred, so it did not affect the final verdict. My rubric interpreted the issue as not sufficiently bounded for a newcomer based on the available evidence. The gold label shows that my scope check was still somewhat too restrictive for this case.

**Check rationale**

`Newcomer-sized scope | Issue body, issue labels, comment thread, and linked/mentioned PR history. | Pass if the issue requests one bounded piece of work. Fail only when the issue is explicitly an umbrella/tracking issue, is purely a usage/support question, has an unresolved design discussion with no maintainer-settled direction, or a maintainer explicitly states that the fix requires changes to core internals. A short or terse issue, missing reproduction steps, or previous abandoned attempts do not by themselves cause failure. | required`

I wrote this check to judge the actual size and boundaries of the requested work instead of judging how polished the issue description is. My first version was too strict because it treated previous abandoned attempts as an automatic failure. I changed it so that abandoned attempts or missing reproduction steps are only warning signs, while clear problems such as umbrella issues, unresolved design work, support questions, or required core-internal changes cause failure.

**Trade-offs**

The revised Newcomer-sized scope check is intentionally less conservative so it does not reject an issue just because the write-up is short, reproduction steps are missing, or earlier contributors did not finish it. The trade-off is that some issues with hidden difficulty can still pass as long as the requested work appears bounded and none of the explicit failure conditions are present. Issue-19 shows that the check can still be too strict in some edge cases, but the revision improved the rubric from 3/4 to 4/4 on the initial test set and contributed to the final 18/20 result.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. The issue's fit to your interests and to the time available.
   Issue #53 fits my interests and the time available because it is a contained Python bug involving phone-number redaction rather than a large architectural change. The issue includes a runnable reproduction, expected behavior, a specific file (`safety/pii_scrubber.py`), and named tests, so there is a clear place to start.
   
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
   My live-mode verdict identified that the repository is active, the issue is bounded, there is no current assignee or open implementation PR, AI-assisted contribution is allowed, and the issue has first-contribution signals. I also considered that the rubric cannot fully predict hidden implementation difficulty or interactions with other redaction patterns until I inspect the code.
   
3. The anticipated difficulty in claiming it.]
I expect the contribution to be manageable because the requested behavior is narrow and the issue already points to the relevant implementation and tests. The main remaining risk is that the regex change could affect other phone-number formats, so I would verify the existing test suite after making the fix.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
