# 📄 Telco Customer Churn Dataset – Data Quality Overview

## 1. Messy Data Issues

While the dataset is mostly clean, a few minor issues were identified that need attention:

### 1.1 Customers with `tenure = 0` and `Churn = 'No'`
- **Meaning:**  
  - `tenure = 0` → Customer has just joined (0 months with the company).  
  - `Churn = No` → Indicates the customer has not left.  

- **Interpretation:**  
  - These customers have literally just signed up, so they couldn’t have churned yet.  
  - Could also indicate missing or incorrect data entries.  

- **Observation:**  
  - There are **11 customers** with this issue:  
    ```
    Index([488, 753, 936, 1082, 1340, 3331, 3826, 4380, 5218, 6670, 6754], dtype='int64')
    ```

### 1.2 `TotalCharges` Data Type Issue
- Currently stored as **object/string**, but values represent numeric charges.  
- Needs to be converted to **float** for analysis.  

---

## 2. Dirty Data Issues

### 2.1 `SeniorCitizen` Column
- Currently coded as `0` (No) and `1` (Yes) instead of textual representation.  
- Recommendation: Convert `0 → No` and `1 → Yes` for clarity and consistency.  

---

## 3. Overall Dataset Quality

- There are **no null values** in the dataset. ✅  
- **SeniorCitizen count:** 1,142 total senior customers. (Ensure this is reasonable for analysis.)  
- Most of the dataset is clean and ready for analysis, which **saves time for data preparation**.  

---

## ✅ Summary

| Issue Type          | Column(s)               | Action Required / Note                          |
|--------------------|------------------------|------------------------------------------------|
| Messy Data         | `tenure`, `Churn`      | Handle 11 customers with `tenure=0` appropriately |
| Messy Data         | `TotalCharges`         | Convert to float for numeric operations       |
| Dirty Data         | `SeniorCitizen`        | Convert 0/1 to 'No'/'Yes'                     |
| Overall Dataset    | All columns            | No nulls, mostly clean, ready for analysis    |

> **Conclusion:** The dataset is largely clean, with minor adjustments needed for a few columns. It is suitable for building churn analysis dashboards and reports.
