# Data Quality & Validation Pipeline

A reusable data quality and validation toolkit — completeness profiling, exact & fuzzy duplicate detection, formatting standardization, and automated QA reporting for structured, field-collected datasets.

Demonstrated end-to-end on a public structured dataset (Titanic passenger records) as a stand-in for real-world field/POI data. The same pipeline logic applies directly to POI, address, and business-listing datasets collected by field teams — where missing fields, inconsistent naming, and duplicate submissions are common data-quality problems.

## What it does

| Stage | What it catches / fixes |
|---|---|
| **Completeness profiling** | Missing-value %, dtype, uniqueness per column |
| **Duplicate detection** | Exact-match duplicates + fuzzy near-duplicate detection (catches inconsistently entered records like `"Cafe Aroma"` vs `"Cafe  Aroma "`) |
| **Formatting standardization** | Whitespace trimming, case normalization, structured sub-field extraction from free text |
| **Rule-based cleaning** | Missing values handled with documented, reversible rules — every imputed row is flagged, never silently changed |
| **Automated QA reporting** | Exportable JSON + CSV summary reports (completeness, duplicates found, fields imputed) |
| **Before/after comparison** | Quantifies the data-quality improvement after cleaning |

## Why this project

Field-collected datasets (POIs, addresses, business listings, etc.) commonly suffer from:
- Missing or incomplete fields
- Duplicate entries submitted by different collectors
- Inconsistent naming/formatting
- No audit trail of what was changed during cleanup

This project builds a small, general-purpose toolkit that addresses all four — with functions designed to be reused on any new batch of collected data, not just this dataset.

## Tech stack

- Python, Pandas, NumPy
- `difflib` for fuzzy/near-duplicate string matching
- JSON/CSV for QA report export

## Project structure

```
├── data_quality_pipeline.ipynb   # Main notebook — full pipeline, end to end
├── Titanic-Dataset.csv           # Sample dataset used for demonstration
├── cleaned_dataset.csv           # Output: cleaned dataset with audit flags
├── qa_report.json                # Output: automated QA summary report
├── column_qa_report.csv          # Output: column-level completeness report
└── README.md
```

## How to run

```bash
pip install pandas numpy ipykernel
```

Open `data_quality_pipeline.ipynb` in VS Code or Jupyter, select a Python kernel, and run all cells top to bottom. Outputs (`cleaned_dataset.csv`, `qa_report.json`, `column_qa_report.csv`) are generated automatically.

## Sample output

The QA report includes metrics such as:
- Overall completeness before/after cleaning
- Number of exact and near-duplicate records flagged
- Fields imputed and the rule used for each
- Records still missing/unknown after cleaning (transparently flagged, not guessed)

## Skills demonstrated

- Data validation for accuracy, completeness, and quality
- Deduplication (exact + fuzzy matching)
- Automation scripting for cleaning and formatting
- QA/error reporting for structured datasets
- Working with CSV/JSON data
