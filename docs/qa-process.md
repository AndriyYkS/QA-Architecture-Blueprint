# QA Process – SimpleShop

This document describes the **QA process** used in the SimpleShop blueprint and can be adapted for real projects.

## 1. SDLC & QA Involvement

We assume an Agile / Scrum-like process:

- QA is involved **from the refinement phase** (shift-left).
- Each user story has:
  - clear acceptance criteria,
  - identified risks,
  - defined test approach (manual/automation).

---

## 2. Workflow Overview

1. **Requirement / User Story Refinement**
   - QA participates in discussions.
   - Risks are identified and added to the risk matrix.
   - High-level test scenarios are drafted.

2. **Design & Implementation**
   - Developers implement features + unit tests.
   - QA prepares or updates:
     - test cases,
     - exploratory charters,
     - automation backlog items.

3. **Testing**
   - Manual testing:
     - checks new functionality,
     - performs exploratory testing.
   - Automation:
     - new tests are added to the framework,
     - existing tests are updated.

4. **CI/CD Execution**
   - On each PR: smoke tests.
   - Nightly: regression suites.

5. **Release Decision**
   - Based on test results, risk assessment, and quality gates.

6. **Feedback & Improvement**
   - Regular reviews of test failures, flaky tests, and coverage.
   - Process and test architecture improvements.

---

## 3. Defect Lifecycle

Typical defect states:

1. New
2. Triaged
3. In Progress
4. Resolved
5. Verified
6. Closed
7. Reopened (if applicable)

Critical/high defects in core flows (login, checkout, cart) **block releases** unless explicitly accepted as risk.

---

## 4. Collaboration

- QA collaborates closely with:
  - Developers (for testability, unit tests, and quick fixes)
  - Product Owners (for risk and priority decisions)
  - DevOps (for CI/CD and environments)

- Code and test changes follow the same **pull request** workflow with code reviews.

---

## 5. Documentation Expectations

- Test strategy and architecture documents are kept in `docs/`.
- Manual test artefacts are in `manual/`.
- Automation documentation is in `automation/docs/`.
- All documents are version-controlled and updated as part of regular work, not “after the fact”。

---

## 6. Continuous Improvement

- Regular **retrospectives** include a QA/test architecture topic.
- Improvement ideas are added to a **QA/Automation backlog**.
- Technical debt in tests (flaky tests, poor patterns) is tracked and systematically reduced.
