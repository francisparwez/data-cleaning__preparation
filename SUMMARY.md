# Project 1 — Data Cleaning & Preparation

## Final Summary

This project prepared the provided raw Excel dataset for analysis through a documented seven-phase data-cleaning workflow.

The process was intentionally based on inspection first, followed by targeted cleaning only where a real data-quality issue was identified.

## Dataset Overview

- Records: 1,200
- Columns: 14
- Date range: 2023-01-01 to 2025-06-30
- Main numeric fields: `Quantity`, `UnitPrice`, `ItemsInCart`, `TotalPrice`
- Date field: `Date`
- Key identifiers: `OrderID`, `CustomerID`, `TrackingNumber`

## Phase 1 — Understanding the Raw Dataset

The raw dataset was loaded and inspected before any cleaning.

Key findings:

- 1,200 rows and 14 columns
- `Date` stored as a datetime field
- Numeric fields stored with appropriate numeric types
- 309 missing `CouponCode` values
- Identifier structures reviewed
- Date range identified as 2023-01-01 to 2025-06-30

No transformations were performed.

**Status: Completed**

## Phase 2 — Data Quality Audit

The raw dataset was audited for:

- Missing values
- Duplicate rows
- Duplicate `OrderID` values
- Date quality
- Numeric quality
- Text consistency
- Identifier formats
- Pricing consistency

Results:

- 309 missing `CouponCode` values
- 0 duplicate rows
- 0 duplicate `OrderID` values
- 0 invalid dates
- No invalid audited numeric values
- No whitespace issues in the audited text fields
- All `TotalPrice` values matched `Quantity × UnitPrice`

No transformations were performed during the audit.

**Status: Completed**

## Phase 3 — Handling Missing Values

The missing `CouponCode` values were investigated before treatment.

Treatment:

```text
Missing CouponCode → NO_COUPON
```

Results:

- 309 missing values replaced
- 0 missing values after treatment
- 1,200 records retained
- 0 records removed

The raw source file was kept unchanged.

**Status: Completed**

## Phase 4 — Check and Remove Duplicates

The cleaned dataset was checked for complete duplicate rows and duplicate `OrderID` values.

Results:

- 0 duplicate rows
- 0 duplicate `OrderID` values
- 0 records removed
- Dataset remained 1,200 × 14

No duplicate-removal transformation was necessary.

**Status: Completed**

## Phase 5 — Correct and Standardize Data Formats

The dataset was reviewed for date, numeric, and text consistency.

Results:

- `Date` remained `datetime64[ns]`
- No date transformation required
- `Quantity` remained `int64`
- `ItemsInCart` remained `int64`
- `UnitPrice` rounded to two decimal places
- `TotalPrice` rounded to two decimal places
- Text and identifiers required no transformation
- Pricing validation remained successful

**Status: Completed**

## Phase 6 — Final Validation

The cleaned dataset was reloaded and tested after all cleaning work.

Final validation:

```text
rows: 1200
columns: 14
missing_values: 0
duplicate_rows: 0
duplicate_order_ids: 0
invalid_dates: 0
pricing_check: True
```

Additional confirmation:

- No missing dates
- `Date` type: `datetime64[ns]`
- Date range: 2023-01-01 to 2025-06-30
- Numeric fields contain no missing values

**Status: Completed**

## Phase 7 — Create the Cleaned Dataset

The validated cleaned dataset was used to create the official final output.

No additional cleaning or transformation was introduced in this phase.

Final output:

```text
data/processed/cleaned_dataset.xlsx
```

The exported file was reloaded and checked again.

### Export Verification

- Shape: 1,200 × 14
- Missing values: 0
- Duplicate rows: 0
- Duplicate `OrderID` values: 0
- Invalid dates: 0
- Pricing check: `True`

**Status: Completed**

## Final Data Changes

Only the following data transformations were applied:

| Area         | Transformation                               |
| ------------ | -------------------------------------------- |
| `CouponCode` | 309 missing values replaced with `NO_COUPON` |
| `UnitPrice`  | Rounded to two decimal places                |
| `TotalPrice` | Rounded to two decimal places                |

No records were removed.

## Final Output

```text
data/processed/cleaned_dataset.xlsx
```

The original raw dataset remained unchanged.

## Final Project Status

**Phases 1 through 7 are complete.**

The dataset is cleaned, standardized where necessary, validated, exported, and ready for downstream analysis.
