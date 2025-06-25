# 🏥 GoHealth EMR Data Engineering Pipeline

This project simulates a real-world EMR (Electronic Medical Records) data pipeline for GoHealth Urgent Care. The pipeline ingests, validates, and transforms patient and visit data from raw CSV extracts into clean outputs that are ready for analysis.

---

## 📁 Data Sources

| File Name        | Description                                                  |
|------------------|--------------------------------------------------------------|
| `patients.csv`   | Master patient list with demographic info                    |
| `visits.csv`     | Visit-level encounters linking patients to care providers    |
| `lab_results.csv`| Lab test results tied to each visit                          |
| `icd_reference.csv` | Reference for ICD diagnosis codes (ICD-10/ICD-9)         |

---

## 🔁 Pipeline Overview

### 1. Ingestion
- Loads raw CSVs using `pandas`
- Validates schema presence and column consistency
- Logs and flags records with missing key fields

### 2. Transformation
- Joins patient + visit + lab + diagnosis code tables
- Handles missing data:
  - Dropping invalid rows (e.g., visits with no patient match)
  - Forward-filling where possible
- Normalizes column formats (dates, strings, categories)
- Creates final output tables for analysis

### 3. Output
- Cleaned, structured tables are written to `outputs/` in CSV format

---

## Schema Layout (Simplified Text Version)

```plaintext
Patient (patient_id PK)
└── Visit (visit_id PK, patient_id FK)
    ├── Lab Results (lab_result_id PK, visit_id FK)
    └── ICD Codes (visit_id FK, code FK)
        └── ICD Reference (code PK)
Design Decisions
Modularized code into ingest, transform, and main scripts

Invalid or unmatched records are excluded from final outputs

Data consistency checks added before joins to ensure integrity

Schema enforced through pre-defined column name checks

External libraries kept minimal to align with HIPAA data handling norms

 Best Practices & Considerations
⚖ HIPAA compliance: Simulated environment assumes anonymized data; no PII persisted in outputs

 Slowly Changing Dimensions (SCD): Not implemented here, but design is compatible with SCD Type 2 tracking if needed

Validation checks ensure robustness in messy CSV conditions (missing values, type mismatches)

 How to Run
bash
Copy
Edit
cd scripts
python main.py
Make sure your virtual environment is active and all required packages are installed.

Dependencies
bash
Copy
Edit
pip install -r requirements.txt
requirements.txt:
pandas

numpy

 File Structure
css
Copy
Edit
gohealth-etl-pipeline/
├── data/
├── outputs/
├── scripts/
│   ├── ingest_data.py
│   ├── transform_data.py
│   └── main.py
├── docs/
│   ├── schema_layout.txt
│   └── design_decisions.md
├── requirements.txt
├── .gitignore
└── README.md

