# Schema Limitations (v0.1)

## 1. Scope Limitations
This schema represents BIM elements at a **static, design-time** level only.

It does not model:
- construction sequencing
- time-series behavior
- execution progress

---

## 2. Inference-Time Limitations
The schema assumes design-stage availability only.

Limitations:
- It cannot represent conditions that emerge during construction
- Any inference beyond design assumptions requires schema extension

---

## 3. Data Quality Limitations
BIM exports may vary across projects and authoring standards.

Known limitations include:
- inconsistent units (mm vs m)
- missing or incomplete parameters
- inconsistent naming conventions

These issues must be handled in the data cleaning stage.

---

## 4. Semantic Limitations
Semantic consistency is not guaranteed across projects.

Examples:
- category naming differences
- family or element naming conventions
- discipline classification variations

A taxonomy or mapping layer may be required in later phases.

---

## 5. Derived Feature Risks
Although derived features (`area`, `volume`) are considered safe in Phase 0:

- Incorrect formulas may introduce noise
- Improper provenance may obscure leakage risk
- Future feature additions may unintentionally use post-outcome data

Derived features must always be reviewed before model training.

---

## 6. Generalization Limitations
Models trained on this schema may not generalize to:
- new building types
- new modeling standards
- different regulatory environments

Concept drift is expected as project characteristics change.

---

## 7. Operational Limitations
Schema evolution introduces operational constraints:

- Schema changes require versioning (`schema_vX`)
- Backward compatibility is not guaranteed
- Pipelines must be revalidated after schema changes

---

## 8. Phase Limitations
Phase 0 schema intentionally excludes:
- cost labels
- schedule labels
- risk outcomes

These will be introduced incrementally in later phases.

---

## 9. Summary
This schema is intentionally minimal.

Its limitations are acceptable for:
- early-stage AI readiness
- feature engineering foundations
- leakage-safe dataset construction