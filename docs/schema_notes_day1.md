# Day 1 — BIM → Table Thinking

## 🎯 Goal
Understand BIM Elements as table records and define basic AI-ready columns.

---

## 1️⃣ BIM Element Concept
- BIM Element = one physical object (object + parameters + behavires)
- In table terms: **1 Element = 1 Row**
- Example: Column, Wall, Beam, Pipe

---

## 2️⃣ Column vs Parameter (Conceptual)
- Element = Entity / Record
- Parameter = Attribute / Column
- Table columns describe the element

---

## 3️⃣ Example Elements (10 samples)
- Structural Column
- Structural Beam
- Structural Slab
- Architectural Wall
- Door
- Window
- Duct
- Pipe
- Light Fixture
- Foundation

---

## 4️⃣ Initial Table Schema (Draft)

| Column Name | Meaning |
|------------|--------|
| element_id | Unique element identifier |
| category | Column / Wall / Pipe |
| level | Building level or storey |
| family | Reusable design family |
| type | Specific type name |
| area | Surface area (if applicable) |
| volume | Solid volume (if applicable) |

---

## 5️⃣ Key Rule
> One element = one row  
> Parameters = table columns
