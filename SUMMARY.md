# Project 1 — Data Cleaning & Preparation

## Phase 1 — Understanding the Raw Dataset

### Overview

The first phase of the project focused on understanding the raw dataset before applying any cleaning or transformation.

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

The missing `CouponCode` values will be considered during the cleaning phase before deciding how they should be treated.

### Phase Status

**Completed**

Phase 2 established the current data-quality state of the raw dataset and provides the basis for the cleaning decisions in the next phase.
