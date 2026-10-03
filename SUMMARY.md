# Project 1 — Data Cleaning & Preparation

## Phase 1 — Understanding the Raw Dataset

### Overview

The first phase focused on understanding the raw dataset before applying any cleaning or transformation.

### Dataset Overview

- Total records: 1,200
- Total columns: 14
- Date range: 2023-01-01 to 2025-06-30
- Numeric fields: Quantity, UnitPrice, ItemsInCart, TotalPrice
- Date field: Date
- Text / identifier fields: OrderID, CustomerID, Product, ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber, CouponCode, ReferralSource

### Initial Findings

- The dataset contains order, customer, product, payment, shipping, and pricing information.
- The `Date` column is stored as a datetime type.
- The main numeric columns are stored as numeric data types.
- `CouponCode` contains 309 missing values.
- The dataset contains several categorical fields, including Product, PaymentMethod, OrderStatus, CouponCode, and ReferralSource.
- OrderID, CustomerID, and TrackingNumber were reviewed to understand their current identifier structure.
- No cleaning or transformation has been performed yet.

### Phase Status

**Completed**

Phase 1 established a baseline understanding of the raw dataset before beginning the data-quality audit.

---

## Phase 2 — Data Quality Audit

### Overview

The second phase focused on auditing the raw dataset for potential data-quality issues before applying any cleaning or transformation.

### Audits Performed

- Missing-value audit
- Duplicate-row audit
- Duplicate OrderID audit
- Date-quality audit
- Numeric-data audit
- Text-consistency audit
- Identifier-format audit
- Logical and business-rule checks

### Findings

- 309 missing values were identified in `CouponCode`.
- No complete duplicate rows were found.
- No duplicate `OrderID` values were found.
- No missing or invalid dates were identified.
- No invalid `OrderID`, `CustomerID`, or `TrackingNumber` formats were identified.
- No invalid numeric values were identified in the audited numeric fields.
- No leading or trailing whitespace issues were detected in the audited text fields.
- All 1,200 `TotalPrice` values matched `Quantity × UnitPrice`.

### Cleaning Decisions

No cleaning changes were applied during the audit phase.

The missing `CouponCode` values were carried forward for investigation and treatment in Phase 3.

### Phase Status

**Completed**

---

## Phase 3 — Handling Missing Values

### Overview

The third phase focused on handling the missing values identified during the data-quality audit.

### Issue Identified

- `CouponCode` contained 309 missing values.
- No other columns contained missing values.

### Investigation

The affected records were reviewed before deciding how the missing values should be handled. The records contained normal order information, and there was no separate field showing whether a coupon had been used.

### Treatment

The 309 missing `CouponCode` values were replaced with `NO_COUPON`.

This treatment was applied to a copy of the raw dataset so that the original source file remained unchanged.

### Result

- Missing `CouponCode` values before cleaning: 309
- Missing `CouponCode` values after cleaning: 0
- Records before cleaning: 1,200
- Records after cleaning: 1,200
- Columns before cleaning: 14
- Columns after cleaning: 14
- Records removed: 0

The cleaned dataset was saved as:

`data/processed/cleaned_dataset.xlsx`

### Phase Status

**Completed**

---

## Phase 4 — Check and Remove Duplicates

### Overview

The fourth phase focused on checking the Phase 3 cleaned dataset for complete duplicate records and duplicate `OrderID` values before making any removal decisions.

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

### Phase Status

**Completed**

Phase 4 confirmed that the cleaned dataset contains no duplicate rows or duplicate `OrderID` values and that no records needed to be removed.

---

## Phase 5 — Correct and Standardize Data Formats

### Overview

The fifth phase focused on validating date, numeric, and text formats in the cleaned dataset and applying transformations only where an actual formatting issue was identified.

### Date Format

- `Date` remained `datetime64[ns]`.
- No missing dates were found.
- Date range remained 2023-01-01 to 2025-06-30.
- No date transformation was required.

### Numeric Format

- `Quantity` remained `int64`.
- `ItemsInCart` remained `int64`.
- `UnitPrice` remained `float64` and was rounded to two decimal places.
- `TotalPrice` remained `float64` and was rounded to two decimal places.
- No missing numeric values were found.
- The `TotalPrice = Quantity × UnitPrice` check remained valid for all 1,200 records.

### Text Format

- No missing text values were found.
- No blank or whitespace-only text values were found.
- No leading or trailing whitespace issues were found.
- No text transformation was required.

### Result

- Final dataset size: 1,200 rows × 14 columns
- Records removed during Phase 5: 0
- Final cleaned dataset: `data/processed/cleaned_dataset.xlsx`
- The saved dataset was reloaded successfully.
- Final pricing validation remained successful after reload.

### Phase Status

**Completed**

Phase 5 completed the required date, numeric, and text format checks and applied the necessary monetary-precision standardization.

---

## Overall Project Status

**Phases 1 through 5 are complete.**

The project has now completed the documented data-cleaning and preparation work covered by the current notebook sequence.
