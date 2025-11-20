# Test Cases – Login – SimpleShop

## 1. Feature Overview

**Feature:** User Login  
**Module/Area:** Authentication  
**Related Requirements:** `REQ-AUTH-001`, `REQ-AUTH-002`  
**Related Risks:** `R1` (see `docs/risk-matrix.md`)

### 1.1 Description

The Login feature allows registered SimpleShop users to access their account using valid credentials (email/username + password). It is a **critical flow**, as it is a prerequisite for checkout, profile management and order history.

### 1.2 In Scope

- Login with valid credentials
- Login with invalid password
- Login with non-existing user
- Field validation (required fields, basic format)
- Basic security behaviour (no detailed security testing here)

### 1.3 Out of Scope

- Password reset (“Forgot password”) – covered in a separate feature
- Account lockout mechanism (only smoke-checked)
- Social login providers

---

## 2. Test Cases

| ID             | Title                                      | Preconditions                      | Steps       | Test Data  | Expected Result      | Priority | Type      | Automation | Status | Comments  |
|----------------|--------------------------------------------|------------------------------------|------------------------------------------------------------|------------|----------------------|----------|-----------|------------|--------|-----------|
| LOGIN-TC-001   | Successful login with valid credentials    | User has a valid, active account   | 1. Navigate to Login page<br>2. Enter valid email<br>3. Enter valid password<br>4. Click **Login**                                                                              | email: valid_user@example.com<br>pwd: *** | User is redirected to Home/Profile page; user’s name or profile icon is displayed; no error messages are shown                                                   | High     | Functional | Yes       | Ready  | Core smoke scenario |
| LOGIN-TC-002   | Error message for invalid password                     | Account exists                                          | 1. Navigate to Login page<br>2. Enter valid email<br>3. Enter invalid password<br>4. Click **Login**                                                                           | email: valid_user@example.com<br>pwd: wrong123 | Error message is displayed (e.g. "Invalid username or password."); user stays on Login page; no session is created                                               | High     | Negative   | Yes       | Ready  |          |
| LOGIN-TC-003   | Error message for non-existing user                    | None                                                    | 1. Navigate to Login page<br>2. Enter non-registered email<br>3. Enter any password<br>4. Click **Login**                                                                      | email: no_user@example.com<br>pwd: any123  | Error message is displayed; user is not logged in                                                                                                                | Medium   | Negative   | Yes       | Ready  |          |
| LOGIN-TC-004   | Required field validation for empty email and password | None                                                    | 1. Navigate to Login page<br>2. Leave email and password empty<br>3. Click **Login**                                                                                            | empty fields                              | Appropriate validation messages are shown for email and password fields; focus or highlight indicates which fields are invalid                                   | Medium   | Functional | Yes       | Ready  | Could be UI-only validation |
| LOGIN-TC-005   | Login is not case-sensitive for email (if specified)   | Requirement states case-insensitive email               | 1. Navigate to Login page<br>2. Enter email with different case (e.g. `VALID_USER@EXAMPLE.COM`)<br>3. Enter valid password<br>4. Click **Login**                                | email: UPPERCASE<br>pwd: valid            | Login succeeds if email comparison is defined as case-insensitive in requirements                                                                               | Low      | Functional | Later     | Draft  | Optional, depends on business rule |
