# Test Architecture – SimpleShop

## 1. Purpose

This document describes the **overall test architecture** for SimpleShop:

- how manual and automated tests are organised,
- how different layers of testing interact,
- how tests integrate with CI/CD and quality gates.

It also acts as a **template** that can be adapted for other products.

---

## 2. High-Level QA Architecture

At a high level, the QA architecture consists of:

- **Manual testing artefacts** (test cases, checklists, exploratory charters)
- **Automated test framework** (UI + API)
- **CI/CD pipelines** that orchestrate test runs
- **Metrics & reporting** to track quality over time

See `/docs/diagrams/qa-architecture.drawio` for a visual overview (to be added).

---

## 3. Test Pyramid

We follow a **modified test pyramid**:

- Unit tests – base (owned by dev team, not part of this repo)
- API tests – main automation layer
- UI tests – thin, focused on critical flows
- Manual exploratory testing – complements automation

Diagram: `/docs/diagrams/test-pyramid.png`.

---

## 4. Manual Test Architecture

Manual artefacts are structured under `/manual`:

- `test-cases/` – detailed test cases for high-risk areas (login, checkout, critical flows).
- `exploratory/` – charters describing **goals, scope, and risks** for exploratory sessions.
- `traceability/` – mapping between requirements, risks, and test coverage.

Principles:

- Use **risk and business impact** to decide where to go deep with manual test design.
- Use **checklists and charters** instead of over-detailed test cases for low-risk areas.
- Keep manual artefacts **lightweight but explicit**.

---

## 5. Automation Framework Architecture

Automation code lives under `/automation/src` and is split into four logical projects:

1. **SimpleShop.Automation.Core**
   - Configuration management
   - WebDriver factory / Playwright drivers
   - Logging & reporting integration
   - Helper utilities (waiting, retries, assertions)

2. **SimpleShop.Automation.API**
   - HTTP clients for Auth, Product, Cart, Checkout APIs
   - Request/response models
   - Common API helpers (status checks, schema validation)

3. **SimpleShop.Automation.UI**
   - Page Object Model for key pages (Login, Products, Cart, Checkout, Profile)
   - Reusable components (header, footer, cart widget)
   - UI interactions abstracted from tests

4. **SimpleShop.Automation.Tests**
   - Test suites:
     - `UI/Smoke`
     - `UI/Regression`
     - `API/Smoke`
     - `API/Regression`
   - Test data builders
   - Tags/categories for CI selection

---

## 6. Environments & Configuration

Configuration is centralised in **Core**:

- `appsettings.json` – base config
- `appsettings.qa.json` – environment-specific overrides

Typical settings:

- Base URLs for UI and API
- Browser / execution mode (headless/non-headless)
- Default timeouts
- Reporting options

The automation framework reads configuration once at startup and exposes strongly-typed settings objects.

---

## 7. CI/CD Integration

CI/CD configuration lives in `/ci-cd`:

- `azure-pipelines-smoke.yml` – runs smoke tests on each pull request.
- `azure-pipelines-regression.yml` – runs extended suites (e.g. nightly).
- `github-actions-ci.yml` – GitHub Actions alternative.

Pipelines:

- checkout code
- restore/build solution
- run tests by category (`Smoke`, `Regression`, etc.)
- publish reports (e.g. Allure, HTML summary)
- apply **quality gates**:
  - all smoke tests must pass
  - no critical test failures allowed
  - flakiness threshold not exceeded (conceptually tracked via metrics)

---

## 8. Metrics and Observability

The test architecture includes hooks for:

- **Test result reporting** (e.g. Allure, NUnit XML)
- **Metrics extraction** (pass/fail trends, flakiness)
- Potential integration with dashboards (Grafana, Azure Boards, etc.)

Metrics are further defined in `/metrics/test-health-dashboard.md`.

---

## 9. Extensibility and Reuse

This blueprint is designed to be:

- **Technology-agnostic on the conceptual level** – same structure can be used with Java/JS/Python frameworks.
- **Product-agnostic** – SimpleShop is just an example domain.
- **Scalable** – additional modules (e.g. mobile, performance tests) can be added without changing the core structure.

To adapt this to a real project:

- Replace SimpleShop domain with the actual product.
- Keep the same document and code structure.
- Adjust test strategy, risk matrix, and quality gates to your context.
