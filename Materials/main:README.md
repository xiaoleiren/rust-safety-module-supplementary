# Rust Safety Teaching Module — Supplementary Materials

This repository contains supplementary materials for the SIGCSE 2027 paper:

**"Compiler-Enforced Safety as a Learning Object: Teaching Memory Safety and Concurrency with Rust"**

## Repository Structure
.
├── README.md # This file
├── supplementary/
│ └── supplementary.pdf # Full supplementary document with individual transition patterns
├── data/
│ ├── concept_probe.csv # Individual pre/post concept probe responses (n=27)
│ ├── compiler_errors.csv # Compiler error classification and persistence data
│ ├── rubric_scores.csv # Individual rubric scores across all four labs
│ └── reflections_anonymized.csv # Anonymized reflection excerpts used in the paper, with thematic codes
└── materials/
├── README.md # Overview of teaching materials
├── lab_handouts/
│ ├── lab1_handout.md
│ ├── lab2_handout.md
│ ├── lab3_handout.md
│ └── lab4_handout.md
├── rubric_templates/
│ ├── lab1_rubric.md
│ ├── lab2_rubric.md
│ ├── lab3_rubric.md
│ └── lab4_rubric.md
├── annotation_worksheets/
│ ├── lab2_annotation_worksheet.md
│ └── lab3_lifetime_worksheet.md
└── starter_code/
└── README.md


## Data Description

### concept_probe.csv

Individual student responses to the 7-item misconception probe, administered pre-module (Week 1) and post-module (Week 5).

- `student_id`: Anonymized student identifier (S01–S27)
- `mc1_pre` through `mc7_pre`: Pre-module responses (0 = incorrect, 1 = correct)
- `mc1_post` through `mc7_post`: Post-module responses (0 = incorrect, 1 = correct)

**Aggregate statistics from this file match Table 1 in the main paper.**

### compiler_errors.csv

Aggregated compiler error data from Labs 2–3 (n=27).

- `error_category`: One of seven error categories
- `total_instances`: Total error instances across all students
- `persistence`: Proportion of errors that recurred after the first attempted fix
- `repair_latency_median`: Median minutes to resolve the error

**Aggregate statistics from this file match Table 2 in the main paper.**

### rubric_scores.csv

Individual rubric scores across all four labs.

- `student_id`: Anonymized student identifier (S01–S27)
- `lab`: Lab number (1–4)
- `dimension`: Rubric dimension (problem_identification, conceptual_explanation, diagnostic_interpretation, repair_verification, uncertainty_awareness)
- `score`: Score (0–3, except uncertainty_awareness which is 0–2)

**Aggregate statistics from this file match Table 5 in the main paper.**

### reflections_anonymized.csv

Anonymized reflection excerpts used in the paper, with thematic codes.

- `student_id`: Anonymized student identifier
- `lab`: Associated lab
- `excerpt`: Anonymized reflection text
- `theme_primary`: Primary thematic code
- `theme_secondary`: Secondary thematic code (if applicable)

## Teaching Materials

The `materials/` directory contains complete teaching materials for the module:

- **Lab Handouts** (Markdown): Student-facing instructions for all four laboratories
- **Rubric Templates** (Markdown): Analytic rubrics for all assessment dimensions
- **Annotation Worksheets** (Markdown): Scaffolding worksheets for diagnostic annotation and lifetime reasoning
- **Starter Code**: A `README.md` explaining the status of starter code during the review process

All materials are provided as Markdown files for easy adaptation and modification.

## Access During Blind Review

This anonymized repository includes all student-facing materials and anonymized data. Complete starter code is withheld during review to avoid revealing author identity.

## Citation

If you use these materials, please cite the associated paper: [Citation details to be added upon publication]

## License

These materials are provided for educational and research purposes. Please contact the authors for any reuse permissions beyond fair use.
