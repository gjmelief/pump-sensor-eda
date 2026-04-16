# Project Plan: Pump Sensor EDA

## Data quality issues found
Summary of findings from notebooks/01_initial_exploration.ipynb

## Data Cleaning

### 1. Drop unnecessary columns
- 'Unnamed: 0' - Original index included in dataset, not needed
- 'sensor_15'- 100% missing values

### 2. Fix dtypes
- Convert 'timestamp' from str to datetime
- Convert 'machine_status' from str to category

### 3. Investigate duplicates
- 5745 duplicate rows (counting both duplicate rows)
- Determine of pattern is recurring or random
- Decision: drop or keep

### 4. Handle outliers and missing values
- 28 sensors with z-score > 3σ
- Investigate relation to machine_status
- Sensors with high missing % (sensor_50: 35%, sensor_51: 7%)
- Decision per sensor: drop, impute or flag

## Open questions
- Are duplicate logging artifacts?
- Are outliers related to BROKEN/RECOVERING states?