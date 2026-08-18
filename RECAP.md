# Blacksmith trial recap

Date: 2026-08-17

## Baseline

- Public repository: https://github.com/Ocean-by-Mosaic/blacksmith-trial
- One dependency-free Node.js smoke test.
- Manual workflow: `.github/workflows/baseline.yml`
- Baseline runner: `ubuntu-latest`
- Successful run: https://github.com/Ocean-by-Mosaic/blacksmith-trial/actions/runs/32090975077
- Local `npm test` also passed.
- No secrets, credentials, or repository secrets were added.

## Onboarding stopping point

Opened https://app.blacksmith.sh and stopped on Blacksmith's sign-in screen,
before clicking **Continue with GitHub**. No browser login, OAuth authorization,
GitHub App installation, payment step, or permission approval was performed.

## What to click next

1. In the open `app.blacksmith.sh` Chrome tab, click **Continue with GitHub**.
2. If GitHub asks you to sign in, complete the GitHub login.
3. Review the Blacksmith OAuth request. If acceptable, click the GitHub
   authorization button (normally **Authorize Blacksmith**).
4. In Blacksmith, choose **Ocean-by-Mosaic** and continue to install the
   Blacksmith GitHub App.
5. On GitHub's installation page, choose **Only select repositories**, select
   **blacksmith-trial**, review the displayed permissions, then click
   **Install & Authorize** (the label may appear as **Install**).
6. Choose the free onboarding option. Blacksmith's pricing page advertises
   3,000 free minutes per month and no card for the trial; if a payment-method
   screen appears, stop and review it before continuing.
7. In Blacksmith's Migration Wizard, select **blacksmith-trial** and the
   **Baseline** workflow. Apply its proposed runner-label change, or edit the
   workflow manually:

   `runs-on: ubuntu-latest` → `runs-on: blacksmith-2vcpu-ubuntu-2404`

8. Push/merge that change, then on GitHub open **Actions** → **Baseline** →
   **Run workflow** → **Run workflow** to run the Blacksmith-backed comparison.

Steps after sign-in are documented expectations; GitHub or Blacksmith may use
slightly different button labels. Always review the actual organization,
repository selection, requested permissions, and any billing screen before
approval.
