# Grading Workflow — Short-Answer Quiz

**Assignment type:** Short-answer quiz (8 questions)
**Total points:** 4.0 (0.5 pt per question, 0.25 pt minimum unit)
**Batch size:** ~55 submissions
**Submission format:** Word documents (.docx / .doc / .rtf)

---

## 1. Pre-Grading Setup

Before grading any submission, confirm the following are in hand:

- [ ] Assignment prompt and all question text
- [ ] Rubric and expected answer elements per question (from instructor)
- [ ] Deadline timestamp (exact date and time)
- [ ] Late penalty policy (confirmed: 1.0 pt per 24-hour period)
- [ ] Partial credit policy (confirmed: 0.25 pt allowed; no lower unit)
- [ ] AI-use policy (confirmed: undisclosed AI use → flag for review)
- [ ] Collaboration policy
- [ ] Output CSV schema approved by TA
- [ ] Student-facing comment tone confirmed (professional, constructive)

Do not begin grading until all items above are confirmed.

---

## 2. Submission Extraction

1. Download all submissions from the course LMS
2. Convert all .doc / .rtf files to .txt (preserve original files)
3. Extract student ID and submission timestamp from each file metadata
4. Flag any submissions that are missing, blank, or unreadable — escalate before grading

---

## 3. Rubric

Each question is worth **0.5 pts**. Apply the following scale:

| Score | Criteria |
|---|---|
| 0.5 | Answer is complete and accurate; correct terminology used |
| 0.25 | Key idea is present but response is incomplete or imprecise; OR correct idea stated but terminology is incorrect |
| 0 | Answer is incorrect, missing, off-topic, or entirely unrelated to the question |

**Partial credit guidance:**
- Award 0.25 when a student demonstrates partial understanding — not just when an answer is "close"
- Do not award 0.25 for restating the question without adding substance
- Do not award 0.25 for a correct answer that is too brief to be verifiable

---

## 4. Late Penalty Tiers

Submission timestamps are compared to the assignment deadline (exact time provided by instructor).

| Hours late | Penalty |
|---|---|
| 0–0 | No penalty |
| >0 to ≤24 | −1.0 pt |
| >24 to ≤48 | −2.0 pts |
| >48 | Flag for instructor decision |

Apply penalty to `total_raw` before computing `final_score`. A score may not go below 0.

---

## 5. Question-by-Question Grading Procedure

For each submission:

1. Read the full submission before scoring any question
2. Score Q1–Q8 in order using the rubric table above
3. Record a one-line rationale for every score (especially 0 and 0.25)
4. Compute `total_raw` = sum of Q1–Q8 scores
5. Apply late penalty if applicable → compute `final_score`
6. Write student-facing comment (see Section 7)
7. Set flag to `REVIEW` if any escalation trigger applies (see Section 8)

---

## 6. Edge Cases

| Situation | Rule |
|---|---|
| Answer addresses a related but different concept | Score 0; note in rationale |
| Answer is correct but question is misread | Score 0.25 if partial understanding is demonstrable |
| Two valid interpretations of the question | Score based on the more charitable interpretation; note uncertainty |
| Answer is extremely brief (1–3 words) but accurate | Score 0.25 unless brevity fully satisfies the rubric criterion |
| Answer contains correct answer plus incorrect content | Score based on the correct portion only; do not penalize the extra content unless it contradicts the correct answer |
| Submission is entirely blank | Score 0 on all questions; note in flag field |

---

## 7. Student-Facing Comment Generation

Write one comment per submission (2–4 sentences). Comments are posted directly to students via the LMS.

**Comment structure:**
1. One sentence summarizing overall performance (positive framing where possible)
2. One sentence identifying the most important gap or error (if any deductions)
3. One sentence referencing a specific improvement or concept for follow-up (if relevant)

**Rules:**
- Reference rubric expectations; do not invent grading criteria
- Do not name individual questions unless necessary for clarity
- Do not use harsh or discouraging language
- Keep to 2–4 sentences; avoid verbose feedback for short-answer quizzes

**Example (strong submission):**
> Good overall performance. Q4 did not address the question asked — review the concept of [topic]. Q2 and Q6 showed the right idea but needed more specific detail to earn full credit.

**Example (weak submission):**
> Several questions were answered with insufficient detail or addressed unrelated concepts. Focus on ensuring each response directly targets the question being asked and uses precise terminology from course materials.

---

## 8. Human Review Triggers

Flag a submission `REVIEW` and do not finalize the score if any of the following apply:

- Submission timestamp is missing or cannot be verified
- Submission appears blank but is not empty (formatting artifacts)
- AI-generated language is suspected (uniform tone, LLM phrasing patterns, no stylistic variation)
- Answer is ambiguous enough that two rubric levels are equally defensible
- Submission contains content suggesting academic integrity concern
- Any question cannot be clearly matched to the rubric

Include a one-line explanation in `grader_note` for every flagged submission.

---

## 9. Output CSV Schema

One row per student. All columns required.

| Column | Type | Description |
|---|---|---|
| `student_id` | string | Anonymized or LMS-provided ID |
| `q1_score` – `q8_score` | float | Score per question (0, 0.25, or 0.5) |
| `total_raw` | float | Sum of Q1–Q8 |
| `late_penalty` | float | Points deducted (0, 1.0, or 2.0) |
| `final_score` | float | `total_raw` − `late_penalty` (min 0) |
| `flag` | string | `OK` or `REVIEW` |
| `grader_note` | string | Internal TA note; not shown to student |
| `lms_comment` | string | Student-facing comment for LMS posting |

---

## 10. Quality Control Checklist

Before submitting the final CSV:

- [ ] All 0.25 scores have a written rationale
- [ ] All `REVIEW` flags have a grader note
- [ ] All late penalties match the timestamp-based tier calculation
- [ ] No `final_score` is below 0
- [ ] Total number of rows matches total number of submissions
- [ ] LMS comments are complete for all non-flagged submissions
- [ ] Flagged submissions are held pending TA/instructor decision

---

## 11. Consistency Notes

- Apply the 0.25 threshold consistently: partial understanding demonstrated — not just "answer was close"
- Do not adjust scores mid-batch based on how other submissions look; apply the rubric as-defined
- If you update the rubric interpretation mid-batch, re-grade all previously scored submissions against the new interpretation
- Keep a running note of any rubric ambiguities encountered for post-batch calibration review
