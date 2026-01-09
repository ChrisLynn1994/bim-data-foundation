# Schema Assumptions (v0.1)

## 1. Purpose
This document records the explicit assumptions required to use the Phase 0
BIM schema (`schema_v0.md`) safely for AI/ML training and inference.

The goal is to prevent data leakage, clarify inference-time availability,
and distinguish raw vs derived features.

---

## 2. Inference-Time Definition
For Phase 0, **inference-time** is defined as:

> The design or pre-construction stage, before construction outcomes
> (cost, duration, progress, changes) are known.

All input features must be available at this time.

---

## 3. Column Availability Assumptions

### 3.1 Columns Assumed Available at Inference-Time (Safe)

The following columns are assumed to exist at inference-time and are safe
for AI/ML training:

- `id`
- `discipline`
- `category`
- `element_name`
- `height`
- `width`
- `depth`
- `material`
- `level`

These fields originate from BIM design data and do not encode future outcomes.

---

### 3.2 Conditionally Available Columns (Derived but Allowed)

The following columns are **derived from geometry**, but are assumed safe
because they depend only on design-time information:

- `area`
- `volume`

**Assumption:**
- These values are computed deterministically from geometry available
  at inference-time.
- No construction or post-design data is used in their computation.

---

### 3.3 Columns Explicitly Excluded (Leakage Prevention)

The following types of columns are **not allowed** in Phase 0 training inputs
and must be excluded if encountered in future datasets:

- actual cost or final quantities
- construction duration or progress
- change orders or variations
- approval or rework indicators

These fields represent post-outcome information and would cause data leakage.

---

## 4. Raw vs Derived Feature Policy

### 4.1 Raw Features
Raw features are directly exported from BIM or source systems without
computational transformation.

**Raw features in schema v0:**
- `id`
- `discipline`
- `category`
- `element_name`
- `height`
- `width`
- `depth`
- `material`
- `level`

---

### 4.2 Derived Features
Derived features are computed from raw features using deterministic logic.

**Derived features in schema v0:**
- `area`
- `volume`

**Assumptions for derived features:**
- The formula is deterministic and documented
- Units are explicit and consistent
- Source columns are known
- Code is version-controlled (e.g. `src/features.py`)

---

## 5. Target Label Assumptions (Forward-Looking)
Target labels (e.g. cost, risk, delay) are **not part of schema v0**.

Assumption:
- Target labels will be introduced only in later phases
- Target labels must never be present as inputs at inference-time

---

## 6. Leakage Prevention Assumptions

The following leakage prevention rules are assumed:

- No column representing future or post-outcome information is used as input
- No derived feature may use future-only data
- All features must be screened against inference-time availability
- Feature provenance must be reviewable before training

---

## 7. Data Splitting Assumptions

Assumption:
- Train/validation/test splits will be performed by project or time,
  not by random element-level sampling, to prevent group leakage.

---

## 8. Unit and Normalization Assumptions

Assumption:
- Numeric geometry fields may require unit normalization
- All units will be normalized during the cleaning stage
- Units must remain explicit or explicitly absent

---

## 9. Summary
Under these assumptions, the Phase 0 schema is considered:

- AI-safe
- Leakage-controlled
- Suitable for downstream ML pipelines

## 📊 Element Core Table
| column_name  | raw / derived | inference-time available | leakage risk | AI/ML reasoning              |
| ------------ | ------------- | ------------------------ | ------------ | ---------------------------- |
| id           | raw           | yes                      | low          | Identifier only, signal မပါ  |
| discipline   | raw           | yes                      | low          | Design-time classification   |
| category     | raw           | yes                      | low          | Element type, safe           |
| element_name | raw           | yes                      | low          | Semantic label only          |
| height       | raw           | yes                      | low          | Geometry from BIM            |
| width        | raw           | yes                      | low          | Geometry from BIM            |
| depth        | raw           | yes                      | low          | Geometry from BIM            |
| area         | ⚠️ derived    | yes                      | low          | Geometry-based, but computed |
| volume       | ⚠️ derived    | yes                      | low          | Geometry-based, but computed |
| material     | raw           | yes                      | low          | Known at design stage        |
| level        | raw           | yes                      | low          | Spatial context, design-time |
