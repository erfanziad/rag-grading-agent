# Grading Workflow: CCT328 Quiz #4
**Course:** CCT328 Project Management — Summer 2026  
**Assignment:** Quiz #4 (Wave Media Case Study)  
**Total Points:** 4.0  
**Grader:** Elnaz Ziad (TA)  
**Workflow Version:** 1.0

---

## Grading Policy Summary (Authoritative Sources)

| Policy | Rule |
|---|---|
| Total score | /4.0 |
| Points per question | 0.5 each (8 questions) |
| Partial credit | 0.25 allowed for partially correct answers |
| Comments | Not required — score only |
| Grace period | Submissions at or before 9:31am = no penalty |
| Late penalty | 20% of quiz value (= 0.8 pts) per 5-minute window past 9:31am |
| Answer key status | Primary reference; full marks track close to key |
| Explanation questions | Must reflect lecture content to receive full marks |

**Sources:** Professor instruction email + Quiz 4 Answers for Grading.docx

---

## Module 1 — Input Intake & Preprocessing

### Required Inputs
- [ ] Student answer sheets (individual `.doc`/`.docx` from Quercus, or batch export)
- [ ] Quercus submission timestamps (per student)
- [ ] Quiz 4 Answers for Grading.docx (answer key — already loaded)
- [ ] Quiz 4.docx (assignment — already loaded)

### Preprocessing Steps
1. **For each submission, extract:**
   - Student full name
   - Student number
   - Submission timestamp (HH:MM EST)
   - Raw text of answers Q1 through Q8

2. **Normalize answer text:**
   - Strip leading/trailing whitespace
   - Lowercase stage names for comparison (e.g., "FORMING" → "forming")
   - Preserve original text for review

3. **Log any extraction failures:**
   - Blank name/student number → flag as MISSING_ID
   - Unreadable file format → flag as EXTRACTION_ERROR, skip to human review
   - Missing answers for specific questions → record as BLANK

4. **Assign a submission ID** (e.g., `Q4_001`, `Q4_002`) for internal tracking

---

## Module 2 — Late Penalty Calculation

**Deadline:** 9:30am EST  
**Grace cutoff:** 9:31am EST (professor-confirmed)

| Submission Time | Penalty | Points Deducted | Max Achievable |
|---|---|---|---|
| ≤ 9:31am | 0% | 0.0 | 4.0 |
| 9:32am – 9:36am | 20% | 0.8 | 3.2 |
| 9:37am – 9:41am | 40% | 1.6 | 2.4 |
| 9:42am – 9:46am | 60% | 2.4 | 1.6 |
| 9:47am – 9:51am | 80% | 3.2 | 0.8 |
| ≥ 9:52am | 100% | 4.0 | 0.0 |

**Formula:** `Final Score = Raw Score × (1 − Penalty Rate)`  
**Rounding:** Round final score to 2 decimal places.

**Edge cases:**
- Timestamp missing or unclear → flag TIMESTAMP_MISSING, apply no penalty until resolved with TA
- Quercus server-side timestamp used (not student's clock)

---

## Module 3 — Rubric: Question-by-Question Scoring Criteria

All scoring decisions must cite specific rubric criteria below. Do not invent criteria.

---

### Q1 — Stage identification for Snapshot A (0.5 pts)
**Expected answer:** Forming

| Score | Criteria |
|---|---|
| 0.5 | Answer is "Forming" or an unambiguous equivalent (e.g., "initial stage," "orientation") |
| 0.25 | Answer describes Forming characteristics without naming the stage, OR uses a vague but directionally correct term |
| 0 | Names a wrong stage (Storming, Norming, Performing, Adjourning), OR blank |

**Evidence anchor:** Snapshot A explicitly states: first meeting, polite/enthusiastic, unclear responsibilities, leader setting structure — all canonical Forming signals.

---

### Q2 — Reasoning for Snapshot A (0.5 pts)
**Expected answer:** Should reference lecture-based Forming characteristics

| Score | Criteria |
|---|---|
| 0.5 | Explanation references ≥ 2 of the following AND connects them to Forming: (a) polite/enthusiastic behavior, (b) unclear roles/responsibilities, (c) reliance on leader for structure/direction, (d) team getting acquainted for the first time |
| 0.25 | References only 1 signal from the snapshot, OR explanation is vague but directionally correct |
| 0 | Explanation is wrong, generic, unsupported, or blank |

**Hallucination guard:** Do not reward signals not present in Snapshot A. Only credit signals drawn from the case text or the answer key.

---

### Q3 — Stage identification for Snapshot B (0.5 pts)
**Expected answer:** Norming  
**Professor instruction:** "Performing" receives 0 — only Norming gets full credit.

| Score | Criteria |
|---|---|
| 0.5 | Answer is "Norming" or an unambiguous equivalent |
| 0.25 | Describes Norming behavior without naming the stage |
| 0 | Any other stage name — including "Performing" — OR blank |

**Note:** Snapshot B does overlap with Performing in some interpretations, but per professor instruction, only Norming is accepted. Flag any "Performing" answers with `REVIEW_NOTE: Student answered Performing — graded 0 per professor policy`.

---

### Q4 — Reasoning for Snapshot B (0.5 pts)
**Expected answer:** Should reference lecture-based Norming characteristics

| Score | Criteria |
|---|---|
| 0.5 | References ≥ 2 of the following AND connects them to Norming: (a) agreed-upon shared workflow, (b) more effective collaboration, (c) appreciation of each other's strengths, (d) increased cohesion / shared norms developing |
| 0.25 | References only 1 signal, OR explanation is vague but directionally correct |
| 0 | Wrong reasoning, generic statement, or blank |

---

### Q5 — Stage identification for Snapshot C (0.5 pts)
**Expected answer:** Adjourning

| Score | Criteria |
|---|---|
| 0.5 | Answer is "Adjourning" or an accepted alternative (e.g., "mourning," "dissolution," "deforming," "transforming" — recognized Tuckman variants) |
| 0.25 | Describes Adjourning characteristics without naming the stage |
| 0 | Wrong stage name OR blank |

**Human review trigger:** Non-standard stage names that are not "Adjourning" → flag for TA judgment.

---

### Q6 — What makes Snapshot C different from the others (0.5 pts)
**Expected answer:** Post-completion; team disbands; emotional tone; closure focus

| Score | Criteria |
|---|---|
| 0.5 | References ≥ 2 of the following: (a) project/task is complete, (b) team disbands/members return to regular roles, (c) emotional component — pride and/or sadness, (d) focus is on closure/reflection rather than task work, (e) only stage about team dissolution not task performance |
| 0.25 | References only 1 distinguishing factor, OR vague but directionally correct |
| 0 | Generic comparison, wrong reasoning, or blank |

---

### Q7 — Gersick's change: what + when (0.5 pts)
**Expected answer:** Significant behavioral/strategic shift at the midpoint (≈ 3 months into the 6-month project)

| Score | Criteria |
|---|---|
| 0.5 | Addresses BOTH: (a) WHAT — a significant shift in behavior, strategy, or approach; AND (b) WHEN — at the midpoint / halfway / at ~3 months / at the 50% mark |
| 0.25 | Addresses only WHAT or only WHEN, not both |
| 0 | Wrong change type, wrong timing, or blank |

**Acceptable phrasings for "when":** "midpoint," "halfway point," "at 3 months," "halfway through," "50% mark," "at the half" — all equivalent.

---

### Q8 — Gersick's reasoning: why (0.5 pts)
**Expected answer:** Initial inertia → time pressure triggers midpoint reassessment → more focused second half

| Score | Criteria |
|---|---|
| 0.5 | References ≥ 2 of the following: (a) initial inertia / patterns set in first half, (b) time pressure / deadline awareness, (c) midpoint as a trigger/wake-up call, (d) reassessment of goals or strategy, (e) more focused/productive second half |
| 0.25 | Vague but directionally correct, OR only 1 element present |
| 0 | Wrong reasoning, generic, or blank |

---

## Module 4 — AI-Use Detection & Flagging

**Context:** The professor confirmed the quiz is completable using generative AI and flagged explanation questions as the key discriminator.

### Detection Signals (any 2+ → flag)
- Answer text closely mirrors answer key phrasing (near word-for-word for explanation questions)
- Unusually complete, structured, or formal language for a short-answer quiz
- All 8 answers are maximally correct with perfect coverage of rubric points
- Explanation answers include theoretical framing not required by the question (e.g., citing Gersick's 1988 study unprompted)

### Action
- **Grade the submission normally** — do not withhold score
- Set `AI_FLAG = Y` in output
- Record `AI_FLAG_REASON` noting which signals were observed
- TA reviews flagged submissions separately

---

## Module 5 — Human Review Triggers

Flag a submission for TA review when any of the following apply:

| Trigger | Review Reason Code |
|---|---|
| Any explanation answer scored 0.25 (borderline) | `BORDERLINE_PARTIAL` |
| Q3 answer is "Performing" | `Q3_PERFORMING_POLICY` |
| Non-standard stage name in Q1, Q3, or Q5 | `NONSTANDARD_STAGE_NAME` |
| Answer placed in wrong question blank | `MISPLACED_ANSWER` |
| Submission timestamp missing or unclear | `TIMESTAMP_MISSING` |
| AI flag set | `AI_SUSPECTED` |
| Total raw score ≤ 1.0 | `VERY_LOW_SCORE` |
| File extraction failure | `EXTRACTION_ERROR` |
| Answer is ambiguous (scorer is uncertain) | `SCORER_UNCERTAIN` |

---

## Module 6 — Score Aggregation

```
Raw Score = Q1 + Q2 + Q3 + Q4 + Q5 + Q6 + Q7 + Q8
          (each 0, 0.25, or 0.5)

Late Deduction = Raw Score × Penalty Rate

Final Score = Raw Score − Late Deduction
Final Score = round(Final Score, 2)
```

---

## Module 7 — Consistency Checks

Run these checks after all submissions are scored:

1. **Cross-submission check:** If two answers with nearly identical text received different scores → flag both for review
2. **Q3 policy check:** Verify all "Performing" answers for Q3 received 0
3. **Late penalty check:** Verify penalty tier applied matches timestamp in Quercus export
4. **Partial credit check:** Review all 0.25 scores — confirm they are not borderline 0.5 or borderline 0
5. **Score distribution check:** Note if overall scores are significantly lower than expected (professor flagged grades are weaker this term)

---

## Module 8 — Output Format

### Per-Student Output Row (CSV)

| Column | Description |
|---|---|
| `submission_id` | Internal ID (e.g., Q4_001) |
| `student_name` | From answer sheet |
| `student_number` | From answer sheet |
| `submission_time` | Timestamp from Quercus |
| `q1` – `q8` | Score for each question (0, 0.25, or 0.5) |
| `raw_score` | Sum of Q1–Q8 (max 4.0) |
| `late_penalty_pct` | Applied penalty (0%, 20%, 40%, etc.) |
| `late_deduction` | Points deducted |
| `final_score` | Score after penalty (max 4.0) |
| `ai_flag` | Y or N |
| `ai_flag_reason` | Text description if flagged |
| `human_review` | Y or N |
| `review_reason` | Review reason code(s) |
| `quercus_comment` | Student-facing feedback text for Quercus SpeedGrader (see Module 10) |

### Summary Report (per grading batch)
- Total submissions graded
- Submissions with late penalties (count + breakdown by tier)
- Submissions flagged for AI use
- Submissions flagged for human review
- Score distribution: min, max, mean, median, % scoring ≥ 3.0

---

## Module 9 — Hallucination Prevention Checklist

Before assigning any score, verify:

- [ ] The scoring criterion used is from **this rubric** (Modules 3), not invented
- [ ] The evidence cited is from the **student's submitted text**, not assumed
- [ ] Stage name acceptance list is followed exactly (Q3: only Norming)
- [ ] Partial credit (0.25) is only awarded when the answer is genuinely partial — not as a compromise between 0 and 0.5
- [ ] Late penalty applied matches the **Quercus timestamp**, not an assumed submission time
- [ ] AI flag is based on observed signals — not on subjective impression alone

If uncertain about any scoring decision: assign `SCORER_UNCERTAIN` flag and defer to TA.

---

## Workflow Execution Order

```
Step 1  →  Receive student submissions (files + Quercus timestamps)
Step 2  →  Preprocessing: extract name, ID, timestamp, Q1–Q8 answers [Module 1]
Step 3  →  Calculate late penalty tier per student [Module 2]
Step 4  →  Score Q1–Q8 per student using rubric [Module 3]
Step 5  →  Apply AI detection check [Module 4]
Step 6  →  Apply human review triggers [Module 5]
Step 7  →  Aggregate raw score + apply late penalty [Module 6]
Step 8  →  Run consistency checks across all submissions [Module 7]
Step 9  →  Generate output CSV + summary report [Module 8]
Step 9.5→  Generate quercus_comment for each submission [Module 10]
Step 10 →  TA reviews all flagged submissions
Step 11 →  TA approves or adjusts flagged scores
Step 12 →  Final scores exported to Quercus gradebook (paste quercus_comment into SpeedGrader)
```

---

## Module 10 — Quercus Feedback Comment Generation

Each submission receives a single `quercus_comment` for direct copy-paste into Quercus SpeedGrader.

**Rules:**
- Student-facing only — no internal codes (AI flags, review codes, TA notes)
- 1–4 sentences max
- Rubric-grounded: deduction phrases reference specific question criteria
- Constructive and professional in tone

### Opening (based on raw_score)
| Raw score | Opening |
|---|---|
| 4.0 | "Good work on Quiz 4 —" |
| 3.5–3.75 | "Good effort on Quiz 4." |
| < 3.5 | "Thank you for submitting Quiz 4." |

### Per-question deduction phrases (appended only when score < 0.5)

| Q | Score | Phrase |
|---|---|---|
| Q1 | 0 | "Q1: Stage name for Snapshot A was not provided." |
| Q2 | 0.25 | "Q2: Your explanation of the Forming stage could be more specific — connect at least two signals from the scenario (e.g., polite behaviour, unclear roles, reliance on the PM for direction)." |
| Q2 | 0 | "Q2: The reasoning for Snapshot A was not answered or did not address the Forming stage." |
| Q3 | 0.25 | "Q3: Snapshot B stage name was partially identified." |
| Q3 | 0 (wrong stage) | "Q3: Snapshot B represents the Norming stage — the scenario describes norms and workflows being established, not peak output." |
| Q3 | 0 (blank) | "Q3: Stage name for Snapshot B was not provided." |
| Q4 | 0.25 | "Q4: Your reasoning for Snapshot B was on the right track — a stronger answer references at least two Norming signals such as the agreed workflow, appreciation of each other's strengths, or developing cohesion." |
| Q4 | 0 | "Q4: The explanation for Snapshot B was not answered or did not address the Norming stage." |
| Q5 | 0 | "Q5: Stage name for Snapshot C was not provided." |
| Q6 | 0.25 | "Q6: Your response for what makes Snapshot C different could be more precise — focus on what is unique to Adjourning: team dissolution, the shift from task work to reflection and closure, and the emotional dimension." |
| Q6 | 0 | "Q6: The distinguishing features of Snapshot C (Adjourning) were not addressed." |
| Q7 | 0.25 | "Q7: Your answer to the Gersick question was partially correct — be sure to address both what changes (a major shift in team behaviour and strategy) and when (at the project midpoint, approximately month 3 for a 6-month project)." |
| Q7 | 0 | "Q7: This question asked about Gersick's Punctuated Equilibrium Model — the expected answer is a significant behavioural/strategic shift occurring at the project midpoint, not variability in other models." |
| Q8 | 0.25 | "Q8: For Gersick's reasoning, the key mechanism is time pressure: teams settle into stable patterns in the first half, then the approaching deadline triggers a reassessment and a more focused second phase." |
| Q8 | 0 | "Q8: This question asked why Gersick's midpoint transition occurs — the answer should reference initial team inertia and the role of deadline-driven urgency, not general team development or interpersonal dynamics." |

### Late suffix (appended when LATE)
"Note: A late submission penalty will be applied to your final grade based on your submission time in Quercus."

### Special-case overrides (by submission_id)
- **goenkavarnan:** "Quiz 4 answers appear to have been placed in the wrong response boxes — only questions 2 and 8 contained responses. Questions 1, 3, 4, 5, 6, and 7 were left blank. Please see your TA if you believe this is an error."
- **mukundwajemimah_LATE:** "This submission was received without a name, student number, or answers. Please contact your TA immediately to resolve this."

### Perfect-score short-circuit
- On-time 4.0: "Good work on Quiz 4 — all 8 questions were answered correctly with clear reasoning grounded in course concepts."
- Late 4.0: "Good work on Quiz 4 — all 8 questions were answered correctly. Note: A late submission penalty will be applied to your final grade based on your submission time in Quercus."

---

## Open Questions / Known Ambiguities

These were resolved before workflow construction but are documented for audit purposes:

| Question | Resolution |
|---|---|
| Partial credit for 0.5-pt questions? | Yes — 0.25 is allowed |
| Is "Performing" acceptable for Q3? | No — 0 per professor instruction |
| Comments required? | Professor said no, but TA generates quercus_comment for optional use in SpeedGrader |
| Late penalty grace period? | 9:31am is fine; penalty starts at 9:32am |
| AI-use policy? | Grade normally, flag for TA review |

---

*Workflow built: 2026-05-27*  
*Grader: Elnaz Ziad (TA), CCT328*  
*Next step: Provide student submissions to begin grading*
