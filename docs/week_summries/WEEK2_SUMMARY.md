## Data Source

This project uses a real BIM export generated from Revit models
(host model with linked models).

The data represents design-time / as-built BIM information
and is stored as raw CSV without any transformation.

## Ingestion Status

- Raw BIM export is stored under `data/raw/`
- CSV has been successfully loaded into pandas
- Column names have been inspected against schema_v0
- No cleaning, filtering, or transformation has been applied

This completes the ingestion phase.

## Key Outcome

- A real BIM export was selected as the data source
- Raw CSV was stored under data/raw without modification
- Dataset was successfully loaded into pandas

## Schema vs Raw Comparsion

- Raw columns were compared against schema_v0
- Missing, extra, and mismatched columns were documented

## Data Quality Snapshot

- Missing values and cardinality were inspected
- Non-physical or tool-generated artifacts were observed
- No data was altered at this stage

## Exit Criteria Validation

| Criteria | Status |
|--------|--------|
| real data ingested | ✅ |
| pandas ingestion complete | ✅ |
| schema alignment reviewed | ✅ |
| raw data untouched | ✅ |

Week 2 ingestion phase is complete and locked.
All data modifications will begin in Week 3
through explicit cleaning rules.
