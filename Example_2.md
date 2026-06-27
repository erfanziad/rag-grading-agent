# Example 2: Open-Ended Assignment Grading

This example demonstrates the RAG Grading Agent applied to an open-ended written assignment. All student names, course codes, and identifying information are anonymized.

---

## Assignment Context

- **Type:** Open-ended written response (2 questions)
- **Total points:** 4 pts (0.5 pt increments)
- **Questions:** 2 open-ended questions requiring analysis and argumentation
- **Submission format:** Word document uploads
- **Late policy:** 0.5 pt deduction per 24-hour period after deadline
- **Partial credit:** Holistic rubric — see scale below
- **Lecture reference requirement:** Responses must reference course material to receive full credit
- **AI-use policy:** AI assistance prohibited; suspected AI use flagged for instructor review

---

## Rubric Summary

Each question is worth 2 pts. The holistic scoring scale per question:

| Score | Description |
|---|---|
| 2.0 | Complete, well-reasoned, references relevant course material accurately |
| 1.5 | Mostly correct with minor gaps; course reference present but surface-level |
| 1.0 | Partial understanding shown; key argument or course connection missing |
| 0.5 | Minimal relevant content; significant gaps or misunderstanding present |
| 0 | Off-topic, missing, or entirely incorrect |

Half-point increments only. No quarter-point credit for this assignment.

---

## Grading Workflow Steps

**Step 1 — Context retrieval**
Before grading, the agent confirmed:
- Rubric criteria and holistic scale
- Lecture material the agent should use as a reference standard
- Late submission policy and timestamp source
- AI-use detection criteria
- Whether responses must reference specific frameworks or only general course themes

**Step 2 — Clarifying questions asked**
The agent asked the following before grading:
- "Should responses that reference the right concept but apply it incorrectly receive partial credit?"
- "Is there a minimum word count or length requirement per question?"
- "Should the lecture reference requirement be strictly enforced (hard cutoff at 1.5 max without it) or treated as a factor?"
- "Are there any example submissions or a model answer available to calibrate the rubric?"

The TA confirmed: lecture reference is required for full credit (hard cutoff at 1.5 without it), no minimum word count, no model answer available.

**Step 3 — Workflow approval**
The TA reviewed the holistic rubric interpretation, the lecture-reference enforcement rule, and the AI-flag escalation criteria before grading started.

**Step 4 — Grading**
The agent read each submission holistically and scored both questions. Rationale was recorded for each score.

---

## Sample Graded Submission (Strong)

**Student ID:** S010 | **Submitted:** On time

**Q1 — Score: 2.0 / 2.0**

> Rationale: The student accurately identified the central tension in the scenario, constructed a clear argument, and explicitly referenced the relevant framework from lecture. The response demonstrated genuine understanding rather than surface recall.

**Q2 — Score: 1.5 / 2.0**

> Rationale: The argument was sound and the student showed understanding of the relevant concept. However, the connection to course material was brief and did not engage with the specific model discussed in lecture. Per the rubric, responses without substantive lecture reference are capped at 1.5.

| | Score |
|---|---|
| Q1 | 2.0 |
| Q2 | 1.5 |
| **Total raw** | **3.5 / 4** |
| Late penalty | 0 |
| **Final score** | **3.5 / 4** |

**Student-facing comment:**
> Q1 was well done — your argument was clearly structured and well-supported by course material. In Q2, your core reasoning was correct, but the connection to the specific framework from lecture was underdeveloped. Engaging more directly with course concepts would have earned full credit here.

---

## Sample Graded Submission (Partial Credit)

**Student ID:** S011 | **Submitted:** 38 hours late

**Q1 — Score: 1.0 / 2.0**

> Rationale: The student identified a relevant theme but the argument was incomplete — only one of the two required components was addressed. No explicit lecture reference was made.

**Q2 — Score: 1.5 / 2.0**

> Rationale: A reasonable response that touched on the right concept. Lecture reference was present but minimal. Per rubric, capped at 1.5 without substantive engagement.

| | Score |
|---|---|
| Q1 | 1.0 |
| Q2 | 1.5 |
| **Total raw** | **2.5 / 4** |
| Late penalty | −1.0 (38 hrs → 2 penalty tiers) |
| **Final score** | **1.5 / 4** |

**Student-facing comment:**
> Q1 needed to address both components of the question — the second part was not engaged with. Including direct reference to course concepts would also strengthen your response. Q2 showed a reasonable understanding, but lecture material should be engaged with more substantively. Note: a late penalty was applied to this submission.

---

## Sample Flagged Submission

**Student ID:** S012 | **Submitted:** On time

**Flag:** `REVIEW — AI suspected`

> Both responses are written in a uniformly structured, impersonal tone inconsistent with in-class writing samples (where available). Q1 uses specific phrasing patterns commonly associated with AI-generated text. Q2 contains a technically accurate framework reference that was not covered in course material — possible evidence of external AI assistance. Recommend instructor review before finalizing score.

---

## Consistency Notes

- The lecture-reference cap (max 1.5 without substantive course connection) was applied uniformly across all submissions
- All half-point scores were used; no quarter-point increments
- Holistic rationale was written for every question on every submission
- 4 submissions were escalated for review out of the batch (2 AI-suspected, 2 borderline rubric cases)
- Late penalties were computed from a single confirmed deadline timestamp
