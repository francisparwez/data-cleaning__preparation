# Change Log

## Project 1 — Data Cleaning & Preparation

| Change ID | Column / Area              | Change                                                                                      | Reason                                                                                                                                                                                       | Impact                                                                                           | Status    |
| --------- | -------------------------- | ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | --------- |
| CL001     | `CouponCode`               | Replaced 309 missing values with `NO_COUPON`                                                | Missing values were present in otherwise complete order records. The dataset does not contain a separate coupon-usage field, so the missing values were treated as no coupon being recorded. | Retained all 1,200 records and removed the missing values from the cleaned dataset.              | Completed |
| CL002     | Duplicate rows / `OrderID` | Checked for complete duplicate rows and duplicate `OrderID` values; no removal was required | Phase 4 required verification of duplicate records and unique order IDs before deciding whether any records should be removed.                                                               | 0 duplicate rows found, 0 duplicate `OrderID` values found, and all 1,200 records were retained. | Verified  |

### Notes

The treatment of missing `CouponCode` values is based on the structure and meaning of the provided dataset. The original raw dataset was not modified. The change was applied only to the working copy used to create the cleaned dataset.

Phase 4 did not introduce any data changes because no complete duplicate rows or duplicate `OrderID` values were found.
