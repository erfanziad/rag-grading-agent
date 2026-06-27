# RAG Grading Agent

An AI-assisted grading system for university courses, built on Claude Code. Designed to reduce TA workload while maintaining rubric consistency, fairness, and transparency across large submission batches.

## What this is

This repo contains the system prompt, grading workflows, and worked examples for a low-hallucination, retrieval-augmented grading assistant. The agent is general-purpose and can be adapted to any course and assignment format.

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
CLAUDE.md           # Core system prompt — agent behavior, RAG principles,
                    # hallucination prevention, and grading philosophy
AGENT.md            # Agent specification and capability summary
Example_1.md        # Worked example: short-answer quiz grading
Example_2.md        # Worked example: open-ended assignment grading
```

## How it works

1. **CLAUDE.md** acts as the persistent system context loaded at the start of every session. It defines the agent's responsibilities, evidence-based grading rules, hallucination prevention policy, and feedback philosophy.

2. **Grading workflows** are built per assignment before any submissions are graded. Each workflow documents:
   - The rubric and scoring scale
   - Late penalty tiers
   - Partial credit rules
   - AI detection criteria
   - Human review triggers
   - Output CSV schema
   - Student-facing comment generation logic

3. **Submissions are extracted** from .doc/.docx/.rtf/.pdf files, parsed, and graded against the rubric. Output is a structured CSV with one row per student.

## Key design principles

- **RAG-first:** All grading decisions are grounded in the provided rubric, answer key, and professor instructions. The agent does not invent criteria.
- **Low hallucination:** The agent is instructed to flag uncertainty, request clarification, and never assume grading rules not explicitly provided.
- **Holistic + consistent:** Partial credit scales and borderline cases are defined upfront so the same standard applies across all submissions.
- **Human-in-the-loop:** Edge cases, ambiguous answers, and AI-suspected submissions are flagged for TA review — not silently resolved.

## Reusing this for a new assignment

1. Start a session with this repo open (CLAUDE.md is auto-loaded)
2. Share the assignment description, rubric, and any professor instructions
3. The agent will ask clarifying questions before building a workflow
4. Once the workflow is approved, share the submissions
5. The agent extracts, grades, and outputs a CSV + summary report

## About

Built by Erfan Ziad, TA and PhD student in Industrial Engineering (Machine Learning).
