# Example 1: Short-Answer Quiz Grading

This example demonstrates the RAG Grading Agent applied to a short-answer quiz. All student names, course codes, and identifying information are anonymized.

---

## Assignment Context

- **Type:** Short-answer quiz
- **Total points:** 4 pts (0.25 pt increments)
- **Questions:** 8 short-answer questions
- **Submission format:** Word document uploads
- **Late policy:** 1 pt deduction per 24-hour period after deadline
- **Partial credit:** Allowed per rubric; 0.25 pt minimum unit
- **AI-use policy:** AI assistance must be disclosed; undisclosed AI use flagged for review

---

## Rubric Summary (Q1–Q8)

Each question is worth 0.5 pts. The scoring scale per question:

| Score | Description |
|---|---|
| 0.5 | Complete, accurate, uses correct terminology |
| 0.25 | Partially correct — key idea present but incomplete or imprecise |
| 0 | Incorrect, missing, or entirely off-topic |

---

## Grading Workflow Steps

**Step 1 — Context retrieval**
Before grading, the agent confirms:
- Rubric criteria per question
- Expected answer elements (instructor-provided)
- Late submission timestamps
- AI-use policy details

**Step 2 — Clarifying questions asked**
The agent asked the following before grading began:
- "Is partial credit allowed for answers that demonstrate understanding but use incorrect terminology?"
- "Should AI-suspected submissions receive a score or be held for review pending instructor decision?"
- "Is the late penalty applied per calendar day or per 24-hour window from the deadline?"

**Step 3 — Workflow approval**
The TA reviewed and approved the workflow, including the partial credit scale and escalation rules, before grading started.

**Step 4 — Grading**
The agent graded each submission question by question, applying the rubric to the extracted text.

---

## Sample Graded Submission

**Student ID:** S001 | **Submitted:** On time

| Question | Score | Rationale |
|---|---|---|
| Q1 | 0.5 | Correctly identified the concept and used accurate terminology |
| Q2 | 0.25 | Key idea present but explanation lacked required detail |
| Q3 | 0.5 | Full credit — accurate and complete |
| Q4 | 0 | Answer referenced an unrelated concept |
| Q5 | 0.5 | Correct |
| Q6 | 0.25 | Partially correct — missed one of two required components |
| Q7 | 0.5 | Correct |
| Q8 | 0.25 | Correct concept, terminology imprecise |
| **Total** | **3.25 / 4** | |
| Late penalty | 0 | On time |
| **Final score** | **3.25 / 4** | |

**Student-facing comment:**
> Strong performance overall. Q4 did not address the question — review the relevant concept. Q2 and Q6 were on the right track but needed more detail to earn full credit. Q8 showed the right idea but terminology precision matters here.

---

## Sample Flagged Submission

**Student ID:** S002 | **Submitted:** 26 hours late

| Question | Score | Rationale |
|---|---|---|
| Q1–Q8 | Scored normally | See below |
| **Total raw** | **3.75 / 4** | |
| Late penalty | −1.0 | Submitted ~26 hrs after deadline |
| **Final score** | **2.75 / 4** | |

**Flag:** `REVIEW — AI suspected`
**Grader note:** Submission language is uniformly formal across all questions with no stylistic variation. Q3 and Q7 responses closely match LLM phrasing patterns. Recommend instructor review before finalizing score.

---

## Consistency Notes

- Partial credit at 0.25 was applied uniformly across all submissions where an answer was partially correct
- All late penalties were computed from the same deadline timestamp
- All AI-flagged submissions were held for TA/instructor review before scores were finalized
- 3 submissions were escalated for review out of the batch
