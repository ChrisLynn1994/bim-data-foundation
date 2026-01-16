# Data Quality Snapshot — Phase 0 / Week 2 / Day 5

## Objective
Capture a point-in-time snapshot of raw BIM data quality
before any cleaning or transformation.

This document informs Week 3 cleaning rules.

---

## Dataset
- Source: Revit export (raw CSV)
- Rows: ~89k
- Columns: 11 (schema_v0 aligned)

---

## 1) Missing Values Overview

| Column | Missing % (approx) | Interpretation |
|---|---:|---|
| id | ~0% | reliable identifier |
| discipline | ~31% | not populated for all elements |
| category | ~31% | missing for some element types |
| element_name | ~13% | mostly present |
| height | ~73% | many elements have no height |
| width | ~89% | sparsely populated |
| depth | ~99% | almost always missing |
| area | ~71% | sparsely populated |
| volume | ~80% | sparsely populated |
| material | ~93% | rarely populated |
| level | ~67% | often missing |

---

## 2) Uniqueness Snapshot

- discipline: low cardinality (controlled set)
- category: high cardinality (BIM taxonomy)
- id: high cardinality (unique identifier)

---

## 3) Obvious Junk / Non-Physical Indicators

Examples observed in `element_name`:
- `<Solid fill>`
- `Diagonal Up`
- `Diagonal Down`

These likely represent symbolic or view-related elements,
not physical BIM components.

---

## 4) Summary

- No structural data corruption detected
- High missingness is expected given mixed element types
- Dataset is suitable for rule-based cleaning in Week 3

No cleaning actions were taken at this stage.
