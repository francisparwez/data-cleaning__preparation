# Change Log

## Project 1 — Data Cleaning & Preparation

| Change ID | Column       | Change                                       | Reason                                                                                                                                                                                       | Impact                                                                              | Status    |
| --------- | ------------ | -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | --------- |
| CL001     | `CouponCode` | Replaced 309 missing values with `NO_COUPON` | Missing values were present in otherwise complete order records. The dataset does not contain a separate coupon-usage field, so the missing values were treated as no coupon being recorded. | Retained all 1,200 records and removed the missing values from the cleaned dataset. | Completed |

### Notes

The treatment of missing `CouponCode` values is based on the structure and meaning of the provided dataset. The original raw dataset was not modified. The change was applied only to the working copy used to create the cleaned dataset.
