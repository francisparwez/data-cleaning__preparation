# DecodeLabs — Data Cleaning & Preparation

This project is part of my Data Analytics Internship at DecodeLabs.

The goal of this project is to take a raw Excel dataset, investigate its data quality, apply only the necessary cleaning and standardization steps, and produce a reliable dataset that is ready for analysis.

The project follows a step-by-step workflow so that each cleaning decision can be inspected and traced back to the original data.

## Project Objective

The project covers:

- Understanding and inspecting the raw dataset
- Auditing missing values and data-quality issues
- Handling missing values appropriately
- Checking duplicate rows and duplicate IDs
- Validating dates, numeric fields, and text fields
- Standardizing monetary precision where needed
- Performing final data-quality validation
- Creating and verifying the final cleaned dataset
- Documenting meaningful changes in the change log

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
│   ├── 06_final_validation.ipynb
│   └── 07_create_cleaned_dataset.ipynb
│
├── .gitignore
├── README.md
├── SUMMARY.md
├── CHANGE_LOG.md
└── requirements.txt
```

## Phase 1 — Understanding the Raw Dataset

The first phase focused on understanding the raw dataset before making any changes.

### What was reviewed

- Dataset size and structure
- Column names
- Data types
- Sample records
- Numeric fields
- Identifier fields
- Categorical fields
- Date coverage

### Findings

- 1,200 records
- 14 columns
- Date range: 2023-01-01 to 2025-06-30
- `Date` is stored as a datetime field
- `Quantity`, `UnitPrice`, `ItemsInCart`, and `TotalPrice` are numeric
- `CouponCode` contains 309 missing values
- `OrderID`, `CustomerID`, and `TrackingNumber` were reviewed as identifier fields
- No cleaning was performed during this phase

**Status: Completed**

## Phase 2 — Data Quality Audit

The second phase audited the raw dataset before applying cleaning changes.

### Checks performed

- Missing values
- Complete duplicate rows
- Duplicate `OrderID` values
- Date quality
- Numeric values
- Text consistency
- Identifier formats
- Pricing consistency

### Findings

- 309 missing `CouponCode` values
- 0 complete duplicate rows
- 0 duplicate `OrderID` values
- 0 missing dates
- 0 invalid dates
- Identifier formats were consistent
- No invalid audited numeric values were identified
- No leading or trailing whitespace issues were found in the audited text fields
- All 1,200 `TotalPrice` values matched `Quantity × UnitPrice`

No cleaning changes were made during the audit itself.

**Status: Completed**

## Phase 3 — Handling Missing Values

The only missing values identified in the audit were in `CouponCode`.

### Decision

The 309 missing `CouponCode` values were replaced with:

```text
NO_COUPON
```

This decision was based on the structure of the dataset. There is no separate field showing whether a coupon was used, so the missing values were treated as no coupon being recorded.

The original raw dataset was kept unchanged. The transformation was applied to a working copy.

### Result

- Missing `CouponCode` values before cleaning: 309
- Missing `CouponCode` values after cleaning: 0
- Records retained: 1,200
- Records removed: 0
- Dataset size: 1,200 × 14

**Status: Completed**

## Phase 4 — Check and Remove Duplicates

The cleaned dataset was checked for:

- Complete duplicate rows
- Duplicate `OrderID` values
- Final duplicate verification
- Row-count changes

### Result

- Duplicate rows: 0
- Duplicate `OrderID` values: 0
- Records removed: 0
- Dataset remained 1,200 × 14

Because no duplicates were found, no duplicate-removal transformation was required.

**Status: Completed**

## Phase 5 — Correct and Standardize Data Formats

This phase checked dates, numeric fields, and text fields and applied transformations only where needed.

### Date

- `Date` remained `datetime64[ns]`
- No missing dates
- Date range remained 2023-01-01 to 2025-06-30
- No date transformation was required

### Numeric fields

- `Quantity` remained `int64`
- `ItemsInCart` remained `int64`
- `UnitPrice` remained `float64`
- `TotalPrice` remained `float64`
- `UnitPrice` and `TotalPrice` were rounded to two decimal places for consistent monetary precision
- Pricing logic remained valid for all 1,200 records

### Text fields

- No missing text values
- No blank or whitespace-only values
- No leading or trailing whitespace issues
- Existing text and identifier formats were kept unchanged because they were already consistent

**Status: Completed**

## Phase 6 — Final Validation

The final cleaned dataset was reloaded and checked after all cleaning and standardization work.

### Validation results

| Check                        |                   Result |
| ---------------------------- | -----------------------: |
| Records                      |                    1,200 |
| Columns                      |                       14 |
| Missing values               |                        0 |
| Duplicate rows               |                        0 |
| Duplicate `OrderID` values   |                        0 |
| Invalid dates                |                        0 |
| Missing dates                |                        0 |
| Date type                    |         `datetime64[ns]` |
| Date range                   | 2023-01-01 to 2025-06-30 |
| Numeric-field missing values |                        0 |
| Pricing business rule        |                   Passed |

**Status: Completed**

## Phase 7 — Create the Cleaned Dataset

The final phase creates the official project output from the already validated cleaned dataset.

No additional cleaning or transformation is performed in this phase.

### Final output

```text
data/processed/cleaned_dataset.xlsx
```

The output file was:

1. Loaded from the validated cleaned dataset
2. Checked before export
3. Exported as the final Excel file
4. Reloaded after export
5. Verified again

### Export verification

- Shape: 1,200 × 14
- Missing values: 0
- Duplicate rows: 0
- Duplicate `OrderID` values: 0
- Invalid dates: 0
- Pricing check: `True`

**Status: Completed**

## Final Cleaning Summary

The project made two actual data changes:

1. 309 missing `CouponCode` values were replaced with `NO_COUPON`
2. `UnitPrice` and `TotalPrice` were rounded to two decimal places

The project did **not** remove any records because duplicate checks found no duplicate rows or duplicate `OrderID` values.

Dates and text fields were left unchanged because they were already valid and consistent.

## Final Deliverable

The final analysis-ready dataset is:

```text
data/processed/cleaned_dataset.xlsx
```

The original raw dataset remains separate and unchanged.

## Final Project Status

**Phases 1 through 7 are complete.**

The cleaned dataset has been created, validated, exported, reloaded, and verified for the required data-quality conditions.
