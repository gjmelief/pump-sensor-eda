# Pump Sensor EDA

Exploratory data analysis and data cleaning on real industrial pump sensor data — applying Pandas and NumPy to the kind of data quality problems a process operator encounters every shift.

---

## 📦 Dataset

This project uses the **Pump Sensor Data** dataset from Kaggle:
[kaggle.com/datasets/nphantawee/pump-sensor-data](https://www.kaggle.com/datasets/nphantawee/pump-sensor-data)

220,320 rows of real pump sensor readings across 52 sensor columns (temperatures, pressures, flows, vibrations). Unlike synthetic datasets, this data contains genuine quality issues: missing values, formatting inconsistencies, and outliers that require deliberate handling.

**Dataset:** `sensor.csv` (~124MB, not tracked in this repo)

Download from Kaggle and place in the `data/` folder to reproduce this analysis.

---

## 🎯 Analysis Goals

This project asks the same questions a maintenance engineer would ask — but answered with data instead of gut feel:

- What does the data quality actually look like across 52 sensor columns?
- Which sensors have missing values, and is the missingness random or systematic?
- Where are the outliers, and do they cluster around known failure events?
- What does normal pump operation look like as a statistical envelope?

---

## 📊 Analysis Phases

| # | Notebook | Focus | Status |
|---|----------|-------|--------|
| 1 | `01_initial_exploration.ipynb` | Data loading, shape, dtypes, missing values, duplicates | 🔄 In progress |
| 2 | `02_data_cleaning.ipynb` | Missing data handling, outlier detection, transformations | ⏳ Planned |
| 3 | `03_analysis.ipynb` | Descriptive stats, correlations, trend analysis | ⏳ Planned |

---

## 🗂️ Repository Structure

```
pump-sensor-eda/
├── data/
│   └── sensor.csv               # Raw dataset (not committed)
├── notebooks/
│   ├── 01_initial_exploration.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_analysis.ipynb
├── pyproject.toml
└── README.md
```

---

## 🔧 Technical Stack

- **Python** 3.x
- **Pandas** — data loading, cleaning, manipulation
- **NumPy** — array operations, statistical functions
- **Matplotlib** — visualization *(Phase 3)*

---

## 🚀 Getting Started

```bash
git clone https://github.com/gjmelief/pump-sensor-eda.git
cd pump-sensor-eda
uv sync
```

Open notebooks in VS Code or run `jupyter notebook` in your terminal.