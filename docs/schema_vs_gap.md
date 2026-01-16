# Schema v0 vs Raw CSV — Gap Report (Phase 0 / Week 2 / Day 4)

## Objective
Compare real raw CSV columns against `schema_v0.md` to identify:
- missing columns
- extra columns
- naming mismatches

Scope note:
- Column-level inspection only (NO transformation, NO cleaning).
- Completeness (null rates) is recorded as an observation, not a schema mismatch.

---

## Inputs
- Schema reference: `docs/schema_v0.md`
- Raw dataset: `schema_v0_export_host_linked.csv` (raw export)

---

## 1) Column Comparison Result

### ✅ Expected Schema v0 Columns (11)
- id
- discipline
- category
- element_name
- height
- width
- depth
- area
- volume
- material
- level

### ✅ Raw CSV Columns (11)
- id
- discipline
- category
- element_name
- height
- width
- depth
- area
- volume
- material
- level

---

## 2) Missing Columns (Schema → Raw)
- None ✅

Result:
- missing_columns = 0

---

## 3) Extra Columns (Raw → Schema)
- None ✅

Result:
- extra_columns = 0

---

## 4) Naming Mismatches
- None ✅

Result:
- naming_mismatches = 0

Notes:
- Column names match exactly (case + spelling).
- This confirms the export aligns with schema_v0 at the column contract level.

---

## 5) Dtype Auto-Inference Check (pandas)
Expected (schema_v0):
- string columns: id, discipline, category, element_name, material, level
- float columns: height, width, depth, area, volume

Observed in pandas (auto-inference):
- string columns inferred as `object`
- float columns inferred as `float64`

Result:
- dtype_mismatches = 0

---

## 6) Observation: Data Completeness (Null Rates)
This is NOT a schema mismatch, but it is a raw data reality signal for Week 3 (Cleaning Rules).

| column | null_pct (approx) | note |
|---|---:|---|
| id | ~0% | good (primary identifier present) |
| discipline | ~31% | missing for many rows |
| category | ~31% | missing for many rows |
| element_name | ~13% | mostly present |
| height | ~73% | mostly missing (many elements likely non-physical / no height) |
| width | ~89% | mostly missing |
| depth | ~99% | almost always missing |
| area | ~71% | mostly missing |
| volume | ~80% | mostly missing |
| material | ~93% | mostly missing |
| level | ~67% | mostly missing |

Interpretation (high-level):
- Column contract is correct (schema alignment OK).
- Completeness varies heavily by element types/categories and export behavior.
- Null-heavy geometry/material fields are expected if many rows represent non-physical or annotation-like elements.

---

## Conclusion
- Schema v0 column contract PASSES against the raw export:
  - missing_columns = 0
  - extra_columns = 0
  - naming_mismatches = 0
  - dtype_mismatches = 0

Next step (Week 3 preview):
- Define cleaning rules that handle null-heavy columns and decide which categories/elements are in-scope for "physical element" analytics.
