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
│   ├── 03_handle_missing_values.ipynb
│   ├── 04_check_remove_duplicates.ipynb
│   ├── 05_correct_standardize_formats.ipynb
│   └── 06_final_validation.ipynb
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
- Dataset size after cleaning: 1,200 rows × 14 columns
- Cleaned dataset: `data/processed/cleaned_dataset.xlsx`

### Phase 3 Status

**Completed**

---

## Phase 4 — Check and Remove Duplicates

The fourth phase focused on checking the Phase 3 cleaned dataset for complete duplicate records and duplicate `OrderID` values.

### Checks Performed

- Complete duplicate-row check
- Duplicate `OrderID` check
- Final duplicate verification
- Row-count verification

### Findings

- No complete duplicate rows were found.
- No duplicate `OrderID` values were found.
- No records were removed.
- The dataset remained at 1,200 records and 14 columns.

### Cleaning Decision

No duplicate-removal action was required because neither the complete-row duplicate check nor the duplicate `OrderID` check identified any duplicates.

### Phase 4 Status

**Completed**

---

## Phase 5 — Correct and Standardize Data Formats

The fifth phase focused on validating date, numeric, and text formats in the cleaned dataset and applying transformations only where an actual formatting issue was identified.

### Date Format

The `Date` column was verified for:

- Datetime data type
- Missing values
- Date range
- Consistent date representation

### Date Findings

- `Date` is stored as `datetime64[ns]`.
- No missing dates were found.
- The date range remains 2023-01-01 to 2025-06-30.
- The date values were already correctly stored, so no date transformation was required.

### Numeric Format

The numeric fields were reviewed for:

- Data types
- Missing values
- Value ranges
- Monetary precision

### Numeric Findings

- `Quantity` remained an integer field.
- `ItemsInCart` remained an integer field.
- `UnitPrice` remained a numeric field and was rounded to two decimal places.
- `TotalPrice` remained a numeric field and was rounded to two decimal places.
- No missing values were found in the numeric fields.

The relationship between price and quantity was rechecked after the transformation:

`TotalPrice = Quantity × UnitPrice`

The validation remained successful for all 1,200 records.

### Text Format

The text and identifier fields were reviewed for:

- Missing values
- Blank values
- Leading or trailing whitespace

### Text Findings

- No missing text values were found.
- No blank or whitespace-only values were found.
- No leading or trailing whitespace issues were found.
- Existing capitalization and identifier formats were kept unchanged because they were already consistent.

### Phase 5 Result

- Date values required no transformation.
- Numeric integer fields required no transformation.
- `UnitPrice` and `TotalPrice` were rounded to two decimal places for consistent monetary precision.
- Text fields required no transformation.
- No records were removed.
- Final dataset size remained 1,200 rows × 14 columns.
- The final cleaned dataset was saved to `data/processed/cleaned_dataset.xlsx`.
- The saved dataset was reloaded and the pricing business rule was verified again successfully.

### Phase 5 Status

**Completed**

---

## Phase 6 — Final Validation

The sixth phase focused on performing the final validation of the cleaned dataset after all cleaning and standardization work was completed.

### Final Checks

The final cleaned dataset was reloaded and checked for:

- Missing values
- Complete duplicate rows
- Duplicate `OrderID` values
- Invalid dates
- Missing dates
- Numeric-field completeness
- Pricing business-rule consistency
- Final row and column counts

### Final Validation Results

- Records: 1,200
- Columns: 14
- Missing values: 0
- Complete duplicate rows: 0
- Duplicate `OrderID` values: 0
- Invalid dates: 0
- Missing dates: 0
- Date data type: `datetime64[ns]`
- Date range: 2023-01-01 to 2025-06-30
- Numeric-field missing values: 0
- Pricing business rule: Passed

The final validation dictionary confirmed:

```text
rows: 1200
columns: 14
missing_values: 0
duplicate_rows: 0
duplicate_order_ids: 0
invalid_dates: 0
pricing_check: True
```

### Phase 6 Status

**Completed**

Phase 6 confirmed that the final cleaned dataset passed the required validation checks and is ready for downstream analysis.

---

## Overall Project Status

**Phases 1 through 6 are complete.**

The project has now completed the documented data-cleaning, preparation, and final validation work covered by the current notebook sequence.

The final cleaned dataset is available at:

`data/processed/cleaned_dataset.xlsx`
