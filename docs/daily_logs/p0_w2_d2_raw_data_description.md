# Raw Data Description — Phase 0 / Week 2 / Day 2

## File
`/data/raw/bim_export_v1.csv`

---

## Source

This dataset is exported from **Autodesk Revit 2024 sample projects**  
provided by Autodesk for learning and demonstration purposes.

The models represent **design-stage BIM data**  
and are not tied to any real construction project.

---

## Export Method

- Tool: Autodesk Revit 2024
- Method: Revit Schedule → Export to CSV
- Scope:
  - Host model elements
  - Sample project–provided element structure
- Exported without any post-processing

---

## Date

2026-01-XX

---

## Description

This file represents the **raw BIM element export**  
directly generated from Revit without:

- transformation
- cleaning
- renaming
- unit normalization
- schema enforcement

The dataset is treated as a **sacred raw input**  
for Phase 0 ingestion and inspection.

---

## Known Characteristics

- Data originates from **Revit sample project modeling standards**
- Element coverage depends on sample model content
- Mixed element categories present:
  - Architecture
  - Structure
  - (limited or no MEP, depending on sample)
- Missing values are expected in multiple parameter columns
- Units are defined by Revit export configuration
- Element population reflects instructional, not production, modeling

---

## Explicit Non-Guarantees

This raw dataset **does not guarantee**:

- full real-world project completeness
- consistency across all element types
- presence of all schema_v0 fields for every element
- real construction accuracy

The dataset is used to validate:
**schema discipline, ingestion logic, and data engineering workflow** —
not to claim production-level BIM fidelity.

---

## Handling Rules

- This file **must remain immutable**
- No edits, fixes, or transformations are allowed
- All processing must occur on derived copies only:
  - `/data/processed/`
  - `/data/features/`

Any modification to this file invalidates
Phase 0 ingestion assumptions.
