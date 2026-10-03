# Change Log

## Project 1 — Data Cleaning & Preparation

| Change ID | Column / Area              | Change                                                                                      | Reason                                                                                                                                                                                                              | Impact                                                                                                                                                         | Status    |
| --------- | -------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| CL001     | `CouponCode`               | Replaced 309 missing values with `NO_COUPON`                                                | Missing values were present in otherwise complete order records. The dataset does not contain a separate coupon-usage field, so the missing values were treated as no coupon being recorded.                        | Retained all 1,200 records and removed the missing values from the cleaned dataset.                                                                            | Completed |
| CL002     | Duplicate rows / `OrderID` | Checked for complete duplicate rows and duplicate `OrderID` values; no removal was required | Phase 4 required verification of duplicate records and unique order IDs before deciding whether any records should be removed.                                                                                      | 0 duplicate rows found, 0 duplicate `OrderID` values found, and all 1,200 records were retained.                                                               | Verified  |
| CL003     | `UnitPrice` / `TotalPrice` | Rounded both price fields to two decimal places                                             | The fields represent monetary values and were standardized to consistent monetary precision.                                                                                                                        | Price values retained their numeric meaning while using two-decimal precision. No records were removed and the final dataset remained 1,200 rows × 14 columns. | Completed |
| CL004     | Final dataset validation   | Reloaded and validated the final cleaned dataset; no additional transformation was required | Final project validation required confirmation that the cleaned dataset contained no missing values, duplicate rows, duplicate `OrderID` values, or invalid dates, and that the pricing business rule still passed. | Confirmed 1,200 rows × 14 columns, 0 missing values, 0 duplicate rows, 0 duplicate `OrderID` values, 0 invalid dates, and a passing pricing check.             | Verified  |

### Notes

The treatment of missing `CouponCode` values is based on the structure and meaning of the provided dataset. The original raw dataset was not modified. The change was applied only to the working copy used to create the cleaned dataset.

Phase 4 did not introduce any data changes because no complete duplicate rows or duplicate `OrderID` values were found.

Phase 5 did not require date or text transformations because the relevant fields were already valid. The only applied transformation in Phase 5 was rounding `UnitPrice` and `TotalPrice` to two decimal places for consistent monetary precision.

The final cleaned dataset was saved as `data/processed/cleaned_dataset.xlsx` and reloaded successfully for final validation.

Phase 6 introduced no additional data transformations. It confirmed the final dataset contained 0 missing values, 0 complete duplicate rows, 0 duplicate `OrderID` values, 0 invalid dates, and a passing pricing business-rule check.
