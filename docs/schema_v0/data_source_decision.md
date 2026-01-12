# Data Source Decision — Phase 0 Week 2 Day 1

## Chosen Source
Real BIM export (Revit / IFC → CSV).

## Reason
- Aligns with real-world BIM complexity
- Exposes missing fields and inconsistent parameters
- Allows validation of schema v0 against real data
- Preferred for professional AI/BIM pipeline development

## Known Constraints
- Some parameters may be missing or inconsistently named
- Instance vs type parameter ambiguity
- Unit inconsistencies depending on export settings

## Missing Data (By Design)
- No cost or schedule outcomes
- No construction-phase information

## Note
Data cleaning and normalization are intentionally deferred to Week 3.
