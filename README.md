# RAG Grading Agent

An AI-assisted grading system for university courses, built on Claude Code. Designed to reduce TA workload while maintaining rubric consistency, fairness, and transparency across large submission batches.

## What this is

This repo contains the system prompt, agent specification, grading workflows, and worked examples for a low-hallucination, retrieval-augmented grading assistant. The agent is general-purpose and can be adapted to any course and assignment format.

The agent handles:
- Rubric interpretation and partial credit decisions
- Per-question scoring with grader notes
- Late penalty calculation
- AI-use detection and flagging
- Human review escalation
- Student-facing feedback generation
- Batch CSV output

## Repo structure

```
AGENT.md                 # Agent specification — capabilities, workflow steps,
                         # output format, hallucination prevention, priority rules

Workflow_Example1.md     # Grading workflow: short-answer quiz
                         # (8 Qs, 4 pts, 0.25 partial credit, late penalty tiers)

Workflow_Example2.md     # Grading workflow: open-ended written assignment
                         # (2 Qs, 4 pts, holistic rubric, lecture reference requirement)

Example_1.md             # Worked example: short-answer quiz
                         # (sample graded submissions, flagged cases, consistency notes)

Example_2.md             # Worked example: open-ended assignment
                         # (strong, partial, and flagged submissions)
```

## How it works

1. **AGENT.md** defines the agent's capabilities, grading workflow steps, hallucination prevention policy, output format, and priority rules. This is the specification layer — read it once to understand how the agent behaves.

2. **Workflow files** are built per assignment before any submissions are graded. Each workflow documents:
   - The rubric and scoring scale
   - Late penalty tiers
   - Partial credit rules
   - Edge case handling
   - AI detection criteria
   - Human review triggers
   - Output CSV schema
   - Student-facing comment templates
   - Quality control checklist

3. **Example files** show the workflow applied to real-format submissions, including strong submissions, partial-credit cases, late submissions, and flagged cases.

4. **Submissions are extracted** from .doc/.docx/.rtf/.pdf files, parsed, and graded against the workflow. Output is a structured CSV with one row per student.

## Key design principles

- **RAG-first:** All grading decisions are grounded in the provided rubric, answer key, and professor instructions. The agent does not invent criteria.
- **Low hallucination:** The agent is instructed to flag uncertainty, request clarification, and never assume grading rules not explicitly provided.
- **Holistic + consistent:** Partial credit scales and borderline cases are defined upfront so the same standard applies across all submissions.
- **Human-in-the-loop:** Edge cases, ambiguous answers, and AI-suspected submissions are flagged for TA review — not silently resolved.

## Reusing this for a new assignment

1. Start a session with this repo open
2. Share the assignment description, rubric, and any professor instructions
3. The agent will ask clarifying questions before building a workflow
4. Once the workflow is approved, share the submissions
5. The agent extracts, grades, and outputs a CSV + summary report

To add a new assignment: create a new `Workflow_<AssignmentName>.md` following the structure in the existing workflow files.

## About

Built by Erfan Ziad, TA and PhD student in Industrial Engineering (Machine Learning).
