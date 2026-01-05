## Project Intent & Operating Contract

### 1. What problem does this repository solve?
This repository addresses the limitation of treating BIM models as drawings.
It reframes BIM as a structured data system by converting BIM elements,
parameters, and relationships into explicit, tabular, and AI-ready datasets.

The goal is to establish a stable data foundation that supports analytics,
automation, and future AI/ML workflows across building and infrastructure projects.

---

### 2. Who is this repository for? (Human + AI)
This repository is designed for:
- BIM professionals who want to think in data, not geometry
- Data engineers who need structured, reliable BIM datasets
- AI/ML engineers who require clean features, labels, and relationships of BIM data
- Automated agents that consume BIM-derived tables and graphs which holding reliable BIM datasets

The schema prioritizes both human interpretability and machine usability.

---

### 3. How is the data structured?
Data is structured using a table-first, relational mindset:

- One BIM Element = One table row
- Element parameters = Table columns
- Element relationships = Join keys or graph edges

Core datasets are normalized and linked using stable identifiers,
allowing relational queries and graph-based reasoning without duplication.

---

### 4. What remains stable over time?
The following principles are treated as immutable:
- Element identity (stable IDs)
- Domain Assets (Buildings, Infrastructure)
- Discipline semantics (Architecture, Structure, MEP)
- Separation of features and labels
- Tool-agnostic schema design
- Reality-based meanings over software-specific fields

Schemas may evolve, but these rules do not change.

---

### 5. How does this repository grow?
This repository evolves incrementally through documented milestones:

- Early stages focus on conceptual clarity and basic schemas
- Later stages introduce richer relationships, context, and validation
- Advanced stages enable graph representations and AI-ready pipelines

Growth is additive and backward-aware, ensuring earlier datasets
remain reusable as the system matures.
