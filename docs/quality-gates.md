# Quality Gates – SimpleShop

Quality gates define **objective criteria** that must be met before:

- merging a pull request,
- promoting a build to a higher environment,
- declaring a release candidate as “ready”.

These gates can be enforced via CI/CD pipelines.

---

## 1. Pull Request (PR) Quality Gates

On each PR:

- ✅ All **unit tests** (not in this repo) must pass.
- ✅ **Smoke automation tests** (UI + API) must pass.
- ✅ No new **critical or high-severity defects** introduced (based on known issues).
- ✅ Code changes are reviewed and approved by at least one peer.

If any gate fails, the PR is blocked until fixed.

---

## 2. QA Environment Build Quality Gates

For a build to be accepted on QA:

- ✅ All PR gates are satisfied.
- ✅ Basic sanity checks on QA environment pass.
- ✅ No open **blocker defects** in the scope of this build.

---

## 3. Regression / Nightly Quality Gates

- ✅ Regression suite pass rate above an agreed threshold (e.g. 95%).
- ✅ No unresolved test failures in high-risk areas (login, cart, checkout).
- ✅ Flakiness rate for regression tests below threshold (e.g. < 3–5%).

If flakiness grows, actions:

- temporarily quarantine tests,
- fix underlying issues,
- refactor test architecture where needed.

---

## 4. Release Candidate Quality Gates

Before promoting a build to production:

- ✅ All critical flows covered by **a mix of automated and manual tests**.
- ✅ No open critical/high defects for the release scope.
- ✅ All release-blocking regression suites have passed.
- ✅ Quality metrics within acceptable ranges:
  - stable trend of test execution times,
  - controlled flakiness,
  - no sudden drop in automation coverage of key flows.

---

## 5. Adaptation to Real Projects

In real commercial projects, these gates should be:

- tailored to **business risk appetite**,
- aligned with **SLAs / SLOs**,
- explicitly implemented in CI/CD (see `/ci-cd` pipelines).
