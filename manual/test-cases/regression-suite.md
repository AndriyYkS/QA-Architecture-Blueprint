# Regression Suite – SimpleShop

This document defines the **regression suite** for SimpleShop as a reusable template.

## 1. Purpose

- Ensure that critical business flows remain stable across releases.
- Provide a **curated list** of test cases (manual + automated) that must be considered for regression.

---

## 2. Regression Scope

| ID         | Area       | Included Test Cases                             | Purpose / Description                                             | Frequency          | Automation Coverage             | In Smoke? | Notes                            |
|------------|------------|-------------------------------------------------|-------------------------------------------------------------------|--------------------|----------------------------------|-----------|-----------------------------------|
| REG-001    | Login      | LOGIN-TC-001, LOGIN-TC-002, LOGIN-TC-003       | Core login success & error handling                              | Every release      | LOGIN-TC-001 (automated UI/API) | Yes       | High risk, core entry point      |
| REG-002    | Cart       | CART-TC-001, CART-TC-002, CART-TC-003          | Add/remove items, update quantities                               | Every release      | Partial                         | No        |                                  |
| REG-003    | Checkout   | CHK-TC-001, CHK-TC-002, CHK-TC-004, CHK-TC-005 | End-to-end ordering and validation                               | Every release      | CHK-TC-001, CHK-TC-004 automated | Yes       | Critical revenue-generating flow |
| REG-004    | Profile    | PROF-TC-001, PROF-TC-002                        | Basic profile view / edit                                        | Every second release | TBD                           | No        | Lower risk                       |

> **Note:**  
> The actual test case details are stored in feature-specific files (e.g. `login-tests.md`, `checkout-tests.md`).  
> This file is a **management-level view** of regression scope.
