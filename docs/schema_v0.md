
This keeps the schema **clean, scalable, and future-proof**.

---

## 3️⃣ Day 2 Canonical → Logical Mapping

### Canonical Level (unchanged)

| Canonical |
|----------|
| id |
| discipline |
| category |
| element |
| parameter |

### Logical Table Level (expanded)
parameter
├── identity parameters
├── geometric parameters
├── material parameters
└── context parameters

| Logical Column | Comes from |
|---------------|-----------|
| id | id |
| discipline | discipline |
| category | category |
| element_name | element |
| height | parameter (geometry) |
| width | parameter (geometry) |
| volume | parameter (geometry) |
| material | parameter (material) |
| level | parameter (context) |

👉 Canonical thinking is preserved  
👉 Table becomes AI-ready

---

## 4️⃣ Example: One Element → One Row

**Element:** Structural Column

| Column | Value |
|------|------|
| id | STR_COL_001 |
| discipline | Structure |
| category | Column |
| element_name | Structural Column |
| height | 4200 |
| width | 400 |
| volume | 1.68 |
| material | Concrete |
| level | L2 |

---

## 5️⃣ Rules for Adding Parameters (Day 2 Rules)

1. Parameters must describe reality, not tools
2. Parameters must have stable meaning over time
3. Geometry parameters must be numeric
4. Text parameters must be categorical
5. Temporary or view-based data is forbidden

---

## 6️⃣ What We Explicitly Do NOT Do (Yet)

- ❌ No family/type split
- ❌ No instance vs type parameters
- ❌ No cost or schedule
- ❌ No AI labels

These belong to **later days / weeks**

---

## ✅ Outcome of Day 2

By the end of Day 2, we can:
- Convert `parameter` from concept → columns
- Build the **first real dataset**
- Keep the schema:
  - Simple
  - Discipline-agnostic
  - Building & infrastructure compatible

---

## ⏭️ Next (Day 3 Preview)

- Identity vs geometry vs context separation
- Minimal “future-proof” parameter set
- CSV schema freeze for Phase 0
