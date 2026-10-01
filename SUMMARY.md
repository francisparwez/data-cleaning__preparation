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
