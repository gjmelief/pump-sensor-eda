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
| 1 | `01_initial_exploration.ipynb` | Data loading, shape, dtypes, missing values, duplicates, z-score outlier scan | ✅ Complete |
| 2 | `02_data_cleaning.ipynb` | Duplicate removal, dtype conversion, outlier/missing analysis by machine status | ✅ Complete |
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

## 📈 Key Findings

- Identified 5,745 duplicate rows via timestamp pattern analysis (1-minute/59-minute recurring logging artifact) and removed them as noise, not signal.
- `sensor_15` is 100% missing and `sensor_50`/`sensor_51` are partially missing (35% and 7% overall) — dropped or flagged depending on downstream use.
- Z-score analysis flagged 28 sensors exceeding 3σ; cross-referencing with the `machine_status` column (NORMAL / BROKEN / RECOVERING) showed all outliers occur during NORMAL operation, and missingness in `sensor_50`/`sensor_51` persists even in NORMAL status (37% and 6% respectively) — ruling out simple "missing because broken" explanations.
- Interpolation strategy for remaining missing values deferred to the analysis phase, once the correlation structure between sensors is better understood.

---

## 🚀 Getting Started

```bash
git clone https://github.com/gjmelief/pump-sensor-eda.git
cd pump-sensor-eda
uv sync
```

Open notebooks in VS Code or run `jupyter notebook` in your terminal.
