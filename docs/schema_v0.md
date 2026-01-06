## 1️⃣ Why Schema Compliance Matters

AI/ML pipelines, data warehouses, and validation tools require:

- explicit data types
- unambiguous descriptions
- unit clarity

Therefore, every dataset column must comply with:
column_name
data_type
description
unit (if any)

## 2️⃣ Canonical → Physical Schema Mapping

### Parameter Expansion Rule (Day 2 Rule)

> `parameter` is decomposed into **multiple physical columns**,  
> each with a **single, stable meaning**.

---

## 3️⃣ Day 2 Canonical Dataset Schema

### 📊 Element Core Table (Draft v0.1)

| column_name | data_type | description | unit |
|------------|----------|-------------|------|
| id | string | Unique identifier for the BIM element | — |
| discipline | string | Engineering discipline (Architecture / Structure / MEP) | — |
| category | string | BIM category of the element (Column, Wall, Pipe, etc.) | — |
| element_name | string | Human-readable name of the physical element | — |
| height | float | Vertical dimension of the element | mm |
| width | float | Horizontal width of the element | mm |
| depth | float | Horizontal depth of the element | mm |
| area | float | Surface area of the element (if applicable) | m² |
| volume | float | Solid volume of the element (if applicable) | m³ |
| material | string | Primary construction material | — |
| level | string | Building level or vertical context | — |

---

## 4️⃣ Mapping Back to Canonical Thinking

| Canonical Concept | Physical Columns |
|------------------|-----------------|
| id | id |
| discipline | discipline |
| category | category |
| element | element_name |
| parameter | height, width, depth, area, volume, material, level |

👉 Canonical model is **preserved**  
👉 Schema is now **machine-validated**

---

## 5️⃣ Example Row (Conceptual)

| id | discipline | category | element_name | height | width | depth | volume | material | level |
|----|-----------|----------|--------------|--------|-------|-------|--------|----------|-------|
| STR_COL_001 | Structure | Column | Structural Column | 4200 | 400 | 400 | 1.68 | Concrete | L2 |

---

## 6️⃣ Day 2 Schema Rules (Strict)

1. Every column must declare a data type
2. Units must be explicit or explicitly absent
3. One column = one meaning
4. No tool-specific or temporary columns
5. Text ≠ numeric (never mix)