# Exploratory Test Charter – Checkout – SimpleShop

**Charter ID:** EXP-CHK-001  
**Area:** Cart & Checkout  
**Tester:** `<Name>`  
**Date:** `<YYYY-MM-DD>`  
**Timebox:** `90 minutes`  

---

## 1. Mission (Charter)

Explore the **Checkout** flow to find issues that could lead to:

- incorrect or failed orders,
- wrong totals or item counts,
- confusing user experience during checkout,
- data inconsistencies between Cart, Checkout and Order History.

---

## 2. Scope

### In Scope

- Checkout with different cart configurations (single item, multiple items, edge quantities)
- Address and payment details validation (as implemented in SimpleShop)
- Order confirmation screen
- Order appearance in Order History

### Out of Scope

- Real payment gateway behaviour (assumed mocked/simulated)
- Detailed tax/currency edge cases
- Deep performance testing

---

## 3. Starting Points & Preconditions

- Test environment: `QA`
- User is registered and can log in
- Access to test data:
  - Products with known prices
  - User accounts with existing order history (optional)

---

## 4. Risks & Focus Areas

- Orders not created or created incorrectly.
- Totals (subtotal, tax, grand total) not matching expectations.
- Items missing or duplicated in the order.
- Confusing or missing validation messages for address/payment fields.

---

## 5. Test Notes

### 5.1 What Was Tested

- Different cart sizes and combinations
- Removing/adding items during checkout
- Entering invalid or borderline input into address and payment fields
- Refreshing or navigating back during Checkout

### 5.2 Issues Found

- `ISSUE-1:` …
- `ISSUE-2:` …

### 5.3 Ideas & Questions

- Suggestions for UX improvements
- Questions about business rules (e.g. shipping calculation)

### 5.4 Data Used

- Example products and quantities
- Example addresses and payment data

---

## 6. Summary

### 6.1 Overall Assessment

Short evaluation of checkout reliability and UX.

### 6.2 Recommendations

- Candidate scenarios for automation (UI + API)
- Areas needing further manual regression focus

### 6.3 Follow-Up Actions

- Defects logged
- New regression test cases identified
- Potential changes to risk matrix entries `R3`, `R4`
