# StudyChat Feasibility Audit 01

**Date:** October 15, 2026  
**Project:** Caldwell University Honors Project  
**Researcher:** Saugat Timalsina

## Purpose

This audit was conducted before finalizing the Honors Project methodology to determine whether the StudyChat dataset contains sufficient longitudinal student–LLM interaction data and linked academic outcomes for the proposed study.

## Dataset Resources Confirmed

The local StudyChat release contains:

- Fall 2024 labeled dialogue data
- Spring 2025 labeled dialogue data
- Fall 2024 normalized grade data
- Spring 2025 normalized grade data
- Assignment materials for A1–A7 in both semesters
- Cleaned student submission archive
- Dialogue-act labels
- Anonymized student identifiers
- Conversation identifiers and timestamps
- Full conversation histories

Raw StudyChat data are kept locally and are not committed to GitHub.

## Overall Dialogue Data

### Fall 2024

- Dialogue rows: 6,864
- Unique students: 84
- Unique chats: 937
- Bad JSON rows: 0

### Spring 2025

- Dialogue rows: 9,987
- Unique students: 119
- Unique chats: 1,277
- Bad JSON rows: 0

### Combined

- Dialogue rows: 16,851
- Students: 203
- Chats: 2,214
- Cross-semester duplicate user IDs: 0

## Assignment Coverage

### Fall 2024

- At least 1 assignment: 84 students
- At least 2 assignments: 83
- At least 3 assignments: 78
- At least 4 assignments: 74
- At least 5 assignments: 58
- At least 6 assignments: 47
- All 7 assignments: 21

### Spring 2025

- At least 1 assignment: 119 students
- At least 2 assignments: 108
- At least 3 assignments: 94
- At least 4 assignments: 82
- At least 5 assignments: 70
- At least 6 assignments: 52
- All 7 assignments: 17

## Academic Outcome Linkage

Both semester grade files contain:

- A1–A7 scores
- E1
- E2
- E3
- aggregate LLM-supported coursework score
- aggregate no-LLM/proctored assessment score

The documented course sequence is:

A1 + A2 → Exam 1  
A3 + A4 → Exam 2  
A5 + A6 + A7 → Final Exam

This creates three natural longitudinal pre-exam periods.

### Fall 2024

- Grade-file students: 70
- Dialogue students: 84
- Students with both dialogue and grades: 65
- Numeric E1 scores: 65/65
- Numeric E2 scores: 65/65
- Numeric E3 scores: 65/65

### Spring 2025

- Grade-file students: 111
- Dialogue students: 119
- Students with both dialogue and grades: 110
- Numeric E1 scores: 110/110
- Numeric E2 scores: 110/110
- Numeric E3 scores: 110/110

### Combined Linked Sample

175 students have both dialogue data and numeric scores for all three exams.

## Longitudinal Block Feasibility

Three provisional blocks were audited:

- Block 1: A1 + A2 → E1
- Block 2: A3 + A4 → E2
- Block 3: A5 + A6 + A7 → E3

### Any StudyChat Use

Combined across semesters:

- Block 1: 157 students
- Block 2: 167 students
- Block 3: 140 students

### Exploratory Threshold: At Least 5 Utterances per Block

- Block 1: 120 students
- Block 2: 145 students
- Block 3: 130 students

Across the 175 linked students:

- At least 2 usable blocks: 142 students
- All 3 usable blocks: 92 students

The 5-utterance threshold was used only as a feasibility diagnostic and is not a final inclusion criterion.

### Exploratory Threshold: At Least 10 Utterances per Block

Across the 175 linked students:

- At least 2 usable blocks: 121 students
- All 3 usable blocks: 74 students

## Dialogue Labels

Frequently observed labels include:

- writing_request > Write Code
- conceptual_questions > Python Library
- conceptual_questions > Programming Language
- conceptual_questions > Computer Science
- contextual_questions > Assignment Clarification
- contextual_questions > Code Explanation
- provide_context > Error Message
- provide_context > Code
- verification > Verify Code

These labels appear suitable for constructing theory-driven help-seeking variables, but the final mapping has not yet been determined.

## Data Quality Finding

The `semester` field was missing from every record in both semester-specific dialogue files.

Observed:

- Fall 2024: 6,864/6,864 records had semester = None
- Spring 2025: 9,987/9,987 records had semester = None

Planned preprocessing correction:

- `f24_labeled_dialogues.jsonl` → semester = `f24`
- `s25_labeled_dialogues.jsonl` → semester = `s25`

This correction will be documented explicitly in preprocessing code.

## Student Submission Archive

The cleaned submission archive contains anonymized student submission directories for multiple assignments in both semesters.

Assignment 1 submissions were not found during the initial archive check.

The primary Honors Project does not depend on student submission files, so this does not currently affect feasibility.

## Feasibility Decision

**Decision: GO**

The dataset contains sufficient linked repeated observations to continue with the proposed longitudinal within-student research design.

### Confirmed

- Dataset access
- Dialogue data
- Academic outcome data
- User-ID linkage
- Three subsequent proctored assessments
- Sufficient repeated observations for longitudinal analysis

### Still Provisional

- Final inclusion threshold
- Final help-seeking category mapping
- Final mixed-effects model specification
- Treatment of sparse student–period observations

## Research Integrity Notes

This is an observational secondary-data study.

Results will be described as associations rather than causal effects.

Logged StudyChat activity will not be interpreted as total AI use because students may have used external AI systems outside the StudyChat platform.

Observable dialogue acts will not automatically be interpreted as internal cognitive states. For example, requesting generated code does not by itself prove cognitive offloading, cheating, or lack of learning.

## Next Step

A later dedicated dataset-analysis phase will examine:

- full dialogue-act taxonomy
- student × block sparsity
- final behavioral-category construction
- inclusion criteria
- mixed-effects model assumptions
- semester-specific robustness analyses

No further detailed dataset auditing is required for the Honors proposal feasibility section.
