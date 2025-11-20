# Requirements Traceability Matrix – SimpleShop

This matrix maps **requirements** to:

- related **risks**,
- **manual test cases**,
- **automated test cases** (logical IDs from automation project),
- and coverage status.

It acts as a **bridge** between business requirements and the test architecture.

---

## 1. Legend

- **Requirement ID (REQ-XXX)** – business or system requirement.
- **Risk ID (R#)** – reference to `docs/risk-matrix.md`.
- **Manual Test Cases** – IDs from `manual/test-cases/*.md`.
- **Automated Tests** – IDs or naming patterns from `SimpleShop.Automation.Tests`.
- **Coverage Status:**  
  - `None` – no tests yet  
  - `Partial` – some aspects tested  
  - `Full` – main acceptance criteria covered  

---

## 2. Traceability Table

| Requirement ID | Requirement Description                                      | Risk ID(s) | Manual Test Cases                            | Automated Tests (Logical IDs)                          | Coverage Status | Comments                              |
|----------------|--------------------------------------------------------------|-----------|----------------------------------------------|--------------------------------------------------------|-----------------|----------------------------------------|
| REQ-AUTH-001   | User must be able to log in with valid email and password   | R1        | LOGIN-TC-001                                 | UI: `LoginSmokeTests.ValidLogin`<br>API: `AuthApiTests.ValidLogin` | Full            | Core smoke scenario                    |
| REQ-AUTH-002   | System must show an error for invalid credentials           | R1        | LOGIN-TC-002, LOGIN-TC-003                   | UI: `LoginSmokeTests.InvalidCredentials`               | Full            |                                        |
| REQ-CART-001   | User can add and remove items from the cart                 | R3        | CART-TC-001, CART-TC-002                     | UI: `CartTests.AddAndRemoveItems`                      | Partial         | More edge cases planned                |
| REQ-CHK-001    | User can successfully complete checkout with valid data     | R4        | CHK-TC-001                                   | UI: `CheckoutSmokeTests.SuccessfulCheckout`            | Full            | High business impact                   |
| REQ-CHK-002    | Checkout must validate required address fields              | R4        | CHK-TC-002                                   | UI: `CheckoutTests.AddressValidation`                  | Full            |                                        |
| REQ-ORD-001    | User can view their recent orders in Order History          | R4        | CHK-TC-005, PROF-TC-001                      | UI: `OrderHistoryTests.OrderVisibleAfterCheckout`      | Partial         | Additional negative tests needed       |

> **Note:**  
> The “Automated Tests” column uses logical names (e.g. `LoginSmokeTests.ValidLogin`) which should correspond to actual test method names in `SimpleShop.Automation.Tests`.  
> This matrix can be exported or mirrored into a test management tool if needed.

---

## 3. Maintenance

- The matrix is updated when:
  - new requirements are added,
  - risks change,
  - new test cases are created,
  - automation coverage grows.

- For real projects, consider:
  - linking requirement IDs to Jira / Azure Boards,
  - generating parts of this matrix automatically from test metadata.
