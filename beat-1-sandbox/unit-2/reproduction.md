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

mattmiara04

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5987290883

Hi! I'd like to work on this issue as my first contribution. I reviewed the reproduction in the issue and the affected `safety/pii_scrubber.py` file. I plan to reproduce the parenthesized US phone-number case first, then, if it reproduces, look into how the phone-number redaction handles the parenthesized format and run the existing PII scrubber tests to make sure any change doesn't break the other supported formats.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5987448504

## Reproduction report

**Environment:**

- Repo: `codepath/pathreview-ai301-fa26-s1`, fresh clone at commit `f89c06fc3ff292df2a04a39ac51319d32a76b779` (main, 2026-09-16)
- OS: Windows 11 Home (10.0.26200), Git Bash
- Python 3.14.3, pytest 9.1.1, structlog 26.1.0
- Setup: a Python venv with the project installed in editable mode with dev extras (`pip install -e ".[dev]"`, the same install step `make setup` runs). I did not run the rest of `make setup` (Docker/Postgres/Redis, `alembic upgrade head`, seed data, frontend install). The scrubber and its tests are pure Python and do not touch the database or API.

**Steps:**

```text
$ git clone https://github.com/codepath/pathreview-ai301-fa26-s1.git
$ cd pathreview-ai301-fa26-s1
$ git checkout f89c06fc3ff292df2a04a39ac51319d32a76b779
$ python -m venv .venv
$ .venv/Scripts/python -m pip install -e ".[dev]"
```

Then I ran the issue's snippet from the repo root:

```text
$ .venv/Scripts/python -c "
from safety.pii_scrubber import PIIScrubber
s = PIIScrubber()
print(repr(s.scrub('Call me at (555) 123-4567 or 555-123-4567')))
print(s.detect('Call me at (555) 123-4567'))
"
```

**Observed:**

```text
'Call me at (555) 123-4567 or [REDACTED]'
2026-10-04 23:07:13 [info     ] pii_detected                   count=0 types=0
[]
```

This matches the issue: the dashed number is redacted, the parenthesized number passes through `scrub()` unchanged, and `detect()` returns no PII for it.

**Test suite:**

```text
$ .venv/Scripts/python -m pytest tests/unit/test_pii_scrubber.py -rx
collected 25 items

tests\unit\test_pii_scrubber.py ..xx.......x.....x....x..                [100%]

=========================== short test summary info ===========================
XFAIL tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_us_phone_number_redaction - issue #53: PII scrubber does not redact parenthesized US phone numbers
XFAIL tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_us_phone_formats - issue #53: PII scrubber does not redact parenthesized US phone numbers
XFAIL tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_detect_phone_pii - issue #53: PII scrubber does not redact parenthesized US phone numbers
XFAIL tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_phone_at_start_of_text - issue #53: PII scrubber does not redact parenthesized US phone numbers
XFAIL tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_mixed_pii_and_text - issue #53: PII scrubber does not redact parenthesized US phone numbers
======================== 20 passed, 5 xfailed in 0.40s ========================
```

The four tests named in the issue xfail as expected. A fifth test, `test_mixed_pii_and_text`, also xfails, and it carries the same `issue #53` xfail reason (`strict=True`) even though the issue doesn't list it.

**Note on `test_mixed_pii_and_text`:** I ran that test on its own with the xfail marker disabled to see the actual failure:

```text
$ .venv/Scripts/python -m pytest "tests/unit/test_pii_scrubber.py::TestPIIScrubber::test_mixed_pii_and_text" --runxfail
E       assert 'Python' in "\n        Professional Background:\n        I worked at TechCorp for [REDACTED]ications.\n        Email: [REDACTED]\n        Phone: [REDACTED]\n        SSN: [REDACTED]\n        I'm skilled in AWS and Kubernetes deployment.\n        "
```

The phone number in that test (`555-123-4567`, dashed) is redacted correctly. The assertion fails because "5 years developing Python appl" is also replaced. My guess is that the `street_address` pattern matches the "pl" in "applications", but I haven't confirmed that. Since the repo marks this test as part of #53, I'm not treating it as out of scope. I'd like a maintainer to say whether it should be fixed under this issue or tracked separately.

**Local attempt at a fix (not yet in a PR):** In my own fork I changed only the `phone_us` pattern in `safety/pii_scrubber.py` to accept a parenthesized area code and a space separator. With that uncommitted change, the same snippet gives:

```text
'Call me at [REDACTED] or [REDACTED]'
2026-10-04 23:07:21 [info     ] pii_detected                   count=1 types=1
[{'type': 'phone_us', 'value': '(555) 123-4567', 'start': 11, 'end': 25}]
```

My fork's copy of `tests/unit/test_pii_scrubber.py` has no xfail markers, so these tests show as plain pass/fail there. Before the change, the five tests above failed (`5 failed, 20 passed`). After the change, the four phone tests pass, and `test_mixed_pii_and_text` still fails with the same `'Python'` assertion shown above (`1 failed, 24 passed`). So the phone-pattern change alone does not resolve that fifth test.

## Eval iterations

**Run history**

`agreement: 3/3 scored items`

`agreement: 14/17 scored items`

`agreement: 3/3 scored items`

`agreement: 1/1 scored items`

`agreement: 4/6 scored items`

`agreement: 17/20 scored items (bar: 18/20: below the bar)`

`agreement: 4/5 scored items`

`agreement: 18/20 scored items (bar: 18/20: PASS)`

**Package analysis**

`pkg-20  gold: reject  verdict: reject  agree: yes`

My original rubric incorrectly accepted `pkg-20` even though the Ghostty repository had a strict AI-use disclosure policy requiring AI usage, the tool used, and the extent of assistance to be disclosed in comments. The reproduction evidence itself was strong, but the candidate comments omitted the required disclosure. I added a dedicated `ai_disclosure` required check and clarified the Comms section of the evidence guide. After the revision, my rubric rejected `pkg-20`, matching the gold label and satisfying the disclosure category floor.

**Check rationale**

`| ai_disclosure | The repo-facts block's AI-use policy, read against the candidate claim comment and repro comment. | Pass when the repository has no applicable AI-disclosure requirement, or when every candidate comment covered by such a requirement contains the disclosure the repository asks for, including the tool and extent of assistance when those details are required. If the repository explicitly requires disclosure for AI-assisted issues or comments and the candidate comments omit it, fail. | required |`

I added this as a separate required check after `pkg-20` showed that my broader `repo_conventions` check was not reliably catching a missing mandatory AI disclosure. I chose an explicit check because disclosure can determine whether a comment is acceptable upstream even when the technical reproduction itself is correct.

**Trade-offs**

Making `ai_disclosure` a required check means a technically excellent reproduction can still be rejected solely because its comment violates a repository's explicit AI-disclosure policy. That is intentional because the assignment is judging whether the package is ready to post upstream, not only whether the technical evidence is correct. I re-ran `pkg-20` after the change and it flipped from the wrong accept verdict to the correct reject verdict. I also re-ran canaries including `pkg-01`, `pkg-04`, and `pkg-14`; those previously correct results remained correct. The final full evaluation scored `18/20`, meeting the bar while preserving the disclosure category.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.