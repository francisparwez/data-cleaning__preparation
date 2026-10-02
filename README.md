# DecodeLabs — Data Cleaning & Preparation

This project is part of my Data Analytics Internship at DecodeLabs.

The goal of this project is to take a raw dataset and prepare it for reliable analysis by identifying and handling data-quality issues such as missing values, duplicate records, and inconsistent data formats. The project also focuses on checking data integrity so that the final dataset can be used with confidence in later analysis.

## Project Objective

The main objectives of this project are:

- Understand and inspect the raw dataset
- Identify missing or null values
- Check for duplicate records and duplicate IDs
- Validate dates and numerical fields
- Check consistency of text-based fields
- Correct data-quality issues where necessary
- Validate the cleaned dataset
- Document the changes made during the cleaning process

## Tools Used

- Python
- Pandas
- Jupyter Notebook
- Microsoft Excel
- Git & GitHub

## Project Structure

```text
data-cleaning__preparation/
│
├── data/
│   ├── raw/
│   │   └── Dataset for Data Analytics.xlsx
│   └── processed/
│       └── cleaned_dataset.xlsx
│
├── notebooks/
│   ├── 01_understand_raw_dataset.ipynb
│   ├── 02_data_quality_audit.ipynb
│   └── 03_handle_missing_values.ipynb
│
├── .gitignore
├── README.md
├── SUMMARY.md
├── CHANGE_LOG.md
└── requirements.txt
```

## Phase 1 — Understanding the Raw Dataset

The first phase focused on understanding the raw dataset before applying any cleaning or transformation.

During this phase, I:

- Loaded the raw Excel dataset using Pandas
- Checked the number of records and columns
- Reviewed the column names and data types
- Inspected sample records and basic statistics
- Documented the purpose of each column
- Reviewed the values in key categorical fields
- Reviewed the identifier fields
- Checked the date range covered by the dataset

### Phase 1 Findings

- The dataset contains 1,200 records and 14 columns.
- The dataset contains order, customer, product, payment, shipping, and pricing information.
- The `Date` column is stored as a datetime type.
- `Quantity`, `UnitPrice`, `ItemsInCart`, and `TotalPrice` are stored as numeric fields.
- `CouponCode` contains 309 missing values, representing 25.75% of the records.
- The date range in the dataset is from 2023-01-01 to 2025-06-30.
- The `OrderID`, `CustomerID`, and `TrackingNumber` fields were reviewed to understand their identifier structure.
- No cleaning or transformation was performed during this phase.

### Phase 1 Status

**Completed**

---

## Phase 2 — Data Quality Audit

The second phase focused on systematically checking the raw dataset for potential data-quality issues before applying any cleaning changes.

The audit covered:

- Missing values
- Duplicate rows
- Duplicate OrderIDs
- Date quality
- Numeric data quality
- Text consistency
- Identifier formats
- Logical and business-rule checks

### Phase 2 Findings

#### Missing Values

- `CouponCode` contains 309 missing values.
- The missing values were inspected but not changed during the audit.
- The remaining columns contained no missing values.

#### Duplicate Records

- No complete duplicate rows were found.
- No duplicate `OrderID` values were found.

#### Date Quality

- The `Date` column is stored as `datetime64[ns]`.
- No missing dates were found.
- No values failed date conversion.
- The dataset covers dates from 2023-01-01 to 2025-06-30.

#### Numeric Data

- `Quantity`, `UnitPrice`, `ItemsInCart`, and `TotalPrice` are stored as numeric data types.
- No invalid quantity values were found.
- No non-positive unit prices were found.
- No negative item counts were found.
- No negative total prices were found.

#### Text Consistency

- The main categorical fields were reviewed for their unique values.
- No leading or trailing whitespace issues were detected in the audited text fields.

#### Identifier Formats

- All `OrderID` values matched the observed `ORD######` pattern.
- All `CustomerID` values matched the observed `C#####` pattern.
- All `TrackingNumber` values matched the observed `TRK########` pattern.

#### Logical Check

- `TotalPrice` was compared with `Quantity × UnitPrice`.
- All 1,200 records matched the expected calculation.

### Phase 2 Status

**Completed**

No cleaning changes were applied during the audit phase. The audit results will be used to determine the appropriate cleaning actions in the next phase.

---

## Next Phase

The next phase will focus on cleaning and preparing the dataset based on the issues identified during the audit. Each cleaning decision will be documented so that the changes can be traced and explained.

---

## Phase 3 — Handling Missing Values

The third phase focused on handling the missing values identified during the data-quality audit.

### Issue Identified

- 309 missing values were found in `CouponCode`.
- No other columns contained missing values.

### Treatment

The affected records were reviewed before making a cleaning decision. Since the dataset does not contain a separate field showing whether a coupon was used, the missing `CouponCode` values were treated as orders where no coupon was recorded and replaced with `NO_COUPON`.

The change was applied to a working copy of the raw dataset so that the original source data remained unchanged.

### Result

- Missing `CouponCode` values before cleaning: 309
- Missing `CouponCode` values after cleaning: 0
- Records retained: 1,200
- Records removed: 0
- Final dataset size: 1,200 rows × 14 columns
- Cleaned dataset: `data/processed/cleaned_dataset.xlsx`

### Phase 3 Status

**Completed**
