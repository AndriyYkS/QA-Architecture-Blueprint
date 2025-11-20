# Risk Matrix – SimpleShop

This document lists key product and quality risks for SimpleShop and can be used as a template for other projects.

## 1. Risk Rating Model

We classify risks by:

- **Likelihood**: Low (1), Medium (2), High (3)
- **Impact**: Low (1), Medium (2), High (3)

Risk score = Likelihood × Impact (1–9).

We prioritise risks with scores **6–9**.

---

## 2. Risk Register

| ID | Area         | Description                                             | Likelihood | Impact | Score | Mitigation / Test Approach                             |
|----|--------------|---------------------------------------------------------|------------|--------|-------|--------------------------------------------------------|
| R1 | Auth         | Users cannot log in with valid credentials              | 2          | 3      | 6     | Smoke UI + API tests for login; detailed manual tests  |
| R2 | Catalog      | Product prices or availability are incorrect            | 2          | 3      | 6     | API regression on product data; UI sanity checks       |
| R3 | Cart         | Items disappear or quantities are wrong                 | 2          | 3      | 6     | End-to-end UI tests for cart; API tests for cart state |
| R4 | Checkout     | Checkout fails or creates incorrect orders              | 2          | 3      | 6     | Critical regression suite on checkout; exploratory     |
| R5 | Performance  | Slow page load or API responses during peak usage       | 2          | 2      | 4     | Basic response time checks; performance outline        |
| R6 | Security     | Users can access other users' data                      | 1          | 3      | 3     | Basic authorization tests; negative-path scenarios     |
| R7 | Stability    | Frequent regressions after releases                     | 2          | 3      | 6     | Strong regression automation; CI quality gates         |
| R8 | UX           | Confusing error messages / validation                   | 2          | 2      | 4     | Exploratory testing focused on usability               |

You can extend this table with project-specific risks.

---

## 3. Linking Risks to Tests

Each risk is mapped to:

- Test suites in `/manual/test-cases` and `/manual/exploratory`
- Automated suites in `/automation/src/SimpleShop.Automation.Tests`

Example:

- **R1 (Auth)**:
  - Manual: `manual/test-cases/login-tests.md`
  - Automation: `UI/Smoke/LoginSmokeTests`, `API/AuthApiTests`

---

## 4. Review and Maintenance

- The risk matrix should be reviewed:
  - at the start of a major release,
  - after significant architectural or business changes,
  - at least once per quarter in a long-running project.

- Changes in risk scores should drive:
  - updates to test strategy,
  - changes in automation priorities,
  - updates to regression scope.
