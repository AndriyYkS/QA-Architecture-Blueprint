# Exploratory Test Charter – Login – SimpleShop

**Charter ID:** EXP-LOGIN-001  
**Area:** Authentication / Login  
**Tester:** `<Name>`  
**Date:** `<YYYY-MM-DD>`  
**Timebox:** `60 minutes`  

---

## 1. Mission (Charter)

Explore the **Login** functionality to discover issues related to:

- error handling for invalid credentials,
- validation messages,
- usability of the login form,
- basic security-related behaviours (no detailed security testing).

---

## 2. Scope

### In Scope

- Standard login form behaviour
- Different combinations of valid/invalid credentials
- Behaviour after multiple failed attempts (to the extent visible on UI)
- Usability aspects (clarity of errors, labels, focus, etc.)

### Out of Scope

- Forgot Password flow
- Social login providers
- Deep security testing (SQL injection, brute force, etc.)

---

## 3. Starting Points & Preconditions

- Test environment: `QA`
- URL: `https://qa.simpleshop.example.com/login`
- Test accounts:
  - Valid user(s)
  - Locked/disabled user (if available)
  - Non-existing emails

---

## 4. Risks & Focus Areas

- Users are **blocked from logging in** despite valid credentials.
- Error messages are confusing, misleading or missing.
- No indication of which field is invalid.
- Inconsistent behaviour between browser types (if tested).

---

## 5. Test Notes

During the session, capture notes in an informal but structured way:

### 5.1 What Was Tested

- Example:
  - Login with valid credentials (Chrome, Firefox)
  - Login with invalid email / password combinations
  - Behaviour after 3–5 failed attempts
  - Browser back/refresh behaviour on login page

### 5.2 Issues Found

- `ISSUE-1:` Short summary, steps to reproduce, expected vs actual.
- `ISSUE-2:` …

### 5.3 Ideas & Questions

- Any observations, potential improvements, questions to PO/Dev.

### 5.4 Data Used

- List of accounts, browsers, devices used during exploration.

---

## 6. Summary

### 6.1 Overall Assessment

Short, high-level summary of the login quality based on this session.

### 6.2 Recommendations

- Areas that require:
  - more automation
  - more manual testing
  - design changes
  - documentation updates

### 6.3 Follow-Up Actions

- New defects logged (IDs)
- New test cases to be added to the regression suite
- Notes for future charters
