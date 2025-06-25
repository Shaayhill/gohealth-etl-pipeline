# gohealth-data-eng-assessment/README.md

# GoHealth Data Engineering Assessment

This project solves a data engineering challenge involving EMR data from multiple sheets in an Excel workbook.

## Project Structure
```
gohealth-data-eng-assessment/
├── data/                       # Place the Excel file here
├── scripts/                    # Core logic files
├── outputs/                   # Output summaries
├── requirements.txt            # Python dependencies
├── README.md
```

##  How to Run

1. **Clone this repo**
```bash
git clone https://github.com/shaayhill/gohealth-data-eng-assessment.git
cd gohealth-data-eng-assessment
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Place the Excel file**
- Save `GoHealth-Data-Eng-Data-Set.xlsx` inside the `data/` directory.

4. **Run the pipeline**
```bash
python scripts/main.py
```

5. **Check results**
- The summary will be saved in `outputs/summary_outputs.csv`

## 🛠️ Technologies Used
- Python 3.8+
- pandas
- openpyxl
