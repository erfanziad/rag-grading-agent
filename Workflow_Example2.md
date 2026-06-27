# Grading Workflow — Open-Ended Assignment

**Assignment type:** Open-ended written response (2 questions)
**Total points:** 4.0 (2.0 pts per question, 0.5 pt minimum unit)
**Batch size:** ~57 submissions
**Submission format:** Word documents (.docx / .doc / .rtf)

---

## 1. Pre-Grading Setup

Before grading any submission, confirm the following are in hand:

- [ ] Assignment prompt and both question texts
- [ ] Holistic rubric (confirmed; see Section 3)
- [ ] Lecture materials to use as reference standard
- [ ] Deadline timestamp (exact date and time)
- [ ] Late penalty policy (confirmed: 0.5 pt per 24-hour period)
- [ ] Lecture reference requirement (confirmed: required for full credit; hard cap at 1.5 without substantive course connection)
- [ ] Partial credit unit (confirmed: 0.5 pt increments only; no quarter-point credit)
- [ ] AI-use policy (confirmed: AI assistance prohibited; suspected use → flag for review)
- [ ] Output CSV schema approved by TA
- [ ] Student-facing comment tone confirmed (professional, constructive, 2–5 sentences)

Do not begin grading until all items above are confirmed.

---

## 2. Submission Extraction

1. Download all submissions from the course LMS
2. Convert all .doc / .rtf files to .txt (preserve original files)
3. Extract student ID and submission timestamp from each file metadata
4. Flag any submissions that are missing, blank, or unreadable — escalate before grading

---

## 3. Rubric (Holistic)

Each question is worth **2.0 pts**. Score holistically using the scale below. Half-point increments only.

| Score | Criteria |
|---|---|
| 2.0 | Complete and well-reasoned response; argument is clearly structured; substantively references relevant course material (specific framework, model, or concept from lecture) |
| 1.5 | Mostly correct with minor gaps; OR correct argument present but course reference is surface-level (e.g., names a concept without engaging with it); OR one of two required components is missing |
| 1.0 | Partial understanding shown; key argument or required component is missing; OR course connection is absent entirely |
| 0.5 | Minimal relevant content; significant gaps or misunderstanding present; answer demonstrates only superficial engagement with the question |
| 0 | Off-topic, missing, or entirely incorrect |

**Lecture reference enforcement:**
- A response that does not include a substantive reference to course material is capped at **1.5 pts maximum**, regardless of argument quality
- "Substantive" means engaging with the concept, model, or framework — not just naming it in passing
- If the correct concept is referenced but applied incorrectly, treat as partial credit (typically 1.0–1.5)

---

## 4. Late Penalty Tiers

Submission timestamps are compared to the assignment deadline (exact time provided by instructor).

| Hours late | Penalty |
|---|---|
| 0 | No penalty |
| >0 to ≤24 | −0.5 pt |
| >24 to ≤48 | −1.0 pt |
| >48 to ≤72 | −1.5 pts |
| >72 | Flag for instructor decision |

Apply penalty to `total_raw` before computing `final_score`. A score may not go below 0.

---

## 5. Question-by-Question Grading Procedure

For each submission:

1. Read both questions and the full submission before scoring anything
2. Score Q1 holistically using the rubric table above
   - Determine the primary score level first, then adjust ±0.5 for edge cases
   - Check whether a substantive lecture reference is present — apply cap if not
3. Score Q2 using the same process
4. Write a one-paragraph rationale for each score (2–3 sentences minimum)
5. Compute `total_raw` = Q1 + Q2
6. Apply late penalty if applicable → compute `final_score`
7. Write student-facing comment (see Section 7)
8. Set flag to `REVIEW` if any escalation trigger applies (see Section 8)

---

## 6. Edge Cases

| Situation | Rule |
|---|---|
| Student references the right concept but applies it to the wrong scenario | Score 1.0 — understanding is partial |
| Student's argument is strong but references a concept not covered in the course | Apply lecture reference cap (max 1.5); flag if the concept is highly advanced (possible AI assistance) |
| Response is very long but unfocused | Score based on the strongest relevant content present; length does not earn credit |
| Response is very short but accurate and complete | Score at face value; length is not a criterion |
| Q1 and Q2 answers are nearly identical | Flag for review — possible copy-paste error or misread of questions |
| Student answers the question in reverse order | Grade the content as written; do not penalize for order |
| Submission is entirely blank | Score 0 on both questions; set flag to `REVIEW` |

---

## 7. Student-Facing Comment Generation

Write one comment per submission (2–5 sentences). Comments are posted directly to students via the LMS.

**Comment structure:**
1. One sentence acknowledging what was done well (or what was attempted)
2. One or two sentences identifying specific gaps tied to rubric criteria
3. One sentence offering a concrete direction for improvement

**Rules:**
- Reference rubric expectations and lecture material; do not invent criteria
- Do not reveal exact scores in the comment
- Do not use harsh or discouraging language
- For flagged submissions, write a placeholder comment and note it pending review

**Example (strong submission):**
> Q1 was well argued and clearly grounded in the course framework — well done. In Q2, your reasoning was correct but the connection to lecture material was underdeveloped; engaging more directly with the specific model discussed in class would have strengthened the response. For future assignments, aim to explicitly name and apply the relevant framework rather than referencing it in passing.

**Example (partial credit submission):**
> Your response to Q1 showed a reasonable understanding of the concept but only addressed one of the two required components. Q2 needed a stronger connection to course material — naming the concept is a start, but explaining how it applies is what earns full credit. Reviewing the relevant lecture section before the next assignment would help.

**Example (weak submission):**
> Both responses were brief and did not substantively engage with the questions as asked. Rubric-level credit requires demonstrating understanding through argument, not just identifying a topic. I'd recommend reviewing the relevant course material and practising applying it to specific scenarios.

---

## 8. Human Review Triggers

Flag a submission `REVIEW` and do not finalize the score if any of the following apply:

- Submission timestamp is missing or cannot be verified
- AI-generated language is suspected (uniform formal tone, no stylistic variation, advanced concepts not covered in the course)
- A score of 1.0 vs 1.5 is not clearly resolvable from the rubric — borderline holistic call
- Response references frameworks or data not plausibly available to students without AI tools
- Submission appears to address a different assignment prompt
- Academic integrity concern of any kind
- Both Q1 and Q2 answers appear to be copied or nearly identical

Include a one-line explanation in `grader_note` for every flagged submission.

---

## 9. Output CSV Schema

One row per student. All columns required.

| Column | Type | Description |
|---|---|---|
| `student_id` | string | Anonymized or LMS-provided ID |
| `q1_score` | float | Score for Q1 (0, 0.5, 1.0, 1.5, or 2.0) |
| `q2_score` | float | Score for Q2 (0, 0.5, 1.0, 1.5, or 2.0) |
| `total_raw` | float | Q1 + Q2 |
| `late_penalty` | float | Points deducted (0, 0.5, 1.0, or 1.5) |
| `final_score` | float | `total_raw` − `late_penalty` (min 0) |
| `flag` | string | `OK` or `REVIEW` |
| `grader_note` | string | Internal TA note; not shown to student |
| `lms_comment` | string | Student-facing comment for LMS posting |

---

## 10. Quality Control Checklist

Before submitting the final CSV:

- [ ] Every Q1 and Q2 score has a written rationale (at least 2 sentences)
- [ ] All scores of 1.5 where the lecture reference cap was applied are noted in `grader_note`
- [ ] All `REVIEW` flags have a grader note explaining why
- [ ] All late penalties match the timestamp-based tier calculation
- [ ] No `final_score` is below 0
- [ ] Total number of rows matches total number of submissions
- [ ] LMS comments are complete for all non-flagged submissions
- [ ] Flagged submissions are held pending TA/instructor decision

---

## 11. Consistency Notes

- The lecture reference cap (max 1.5 without substantive course connection) applies to every submission without exception
- Holistic scoring means assessing the overall response — do not mechanically average sub-components
- If you notice that you are interpreting the rubric more leniently or strictly mid-batch, stop, re-read the rubric definition, and re-grade any affected submissions
- Keep a running note of borderline cases for post-batch calibration with the instructor
- If you are uncertain whether a lecture reference is "substantive," default to 1.5 (not 2.0) and note it in `grader_note`
