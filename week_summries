# Phase 0 — Week 1 Summary
## Schema Mindset Lock

### Objective
The objective of Week 1 was to define a clear, AI-safe schema mindset
for representing BIM data as a machine-learning-ready dataset.

---

## Key Outcomes

### 1. Element Row Concept
- One BIM element is represented as one dataset row
- Rows are atomic and non-aggregated
- Suitable for AI training and inference

This concept establishes the foundation for all downstream pipelines.

---

### 2. Canonical Schema v0
- Canonical concepts were translated into physical columns
- Each column has:
  - a single meaning
  - an explicit data type
  - explicit or explicitly absent units

Schema v0 focuses on design-time BIM attributes only.

---

### 3. AI Leakage Review
The schema was reviewed using an AI training and inference mindset.

Actions taken:
- Defined inference-time explicitly (design / pre-construction)
- Identified raw vs derived features
- Excluded future-only and outcome-related fields

Result:
- No known leakage risks in schema v0

---

### 4. Assumptions and Limitations
Explicit documentation was added to clarify:
- what data is assumed available at inference-time
- what the schema cannot represent
- how derived features must be handled

Documents:
- `docs/schema_assumptions.md`
- `docs/schema_limitations.md`

---

## Exit Criteria Validation

| Criteria | Status |
|--------|--------|
| schema_v0.md exists | ✅ |
| element row concept documented | ✅ |
| assumptions explicit | ✅ |
| repo readable by stranger | ✅ |

---

## Final Status
**Phase 0 — Week 1 is complete and locked.**

No further schema changes should be made without versioning
(`schema_vX`) and explicit review.
