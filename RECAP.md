# Blacksmith trial recap

Date: 2026-08-17

## Baseline

- Public repository: https://github.com/Ocean-by-Mosaic/blacksmith-trial
- One dependency-free Node.js smoke test.
- Manual workflow: `.github/workflows/baseline.yml`
- Baseline runner: `ubuntu-latest`
- Successful run: https://github.com/Ocean-by-Mosaic/blacksmith-trial/actions/runs/32090975077
- Dispatch-to-completion: 16 seconds; assigned job runtime: 8 seconds.
- Local `npm test` also passed.
- No secrets, credentials, or repository secrets were added.

## Blacksmith trial

- GitHub authorization was completed by the user.
- The Blacksmith GitHub App was installed only on
  `Ocean-by-Mosaic/blacksmith-trial`.
- No billing screen appeared.
- Runner tested: `blacksmith-2vcpu-ubuntu-2404`, the smallest current
  Blacksmith x64 Ubuntu runner.
- Workflow commit: `01a04f8`
- Trial run: https://github.com/Ocean-by-Mosaic/blacksmith-trial/actions/runs/32092321097
- Result: no runner was assigned and no workflow step started. The job remained
  queued for 6 minutes 16 seconds and was then cancelled.
- GitHub reported `runner_id: 0`, an empty runner name, and no steps. This is a
  runner provisioning/registration failure, not a test failure or useful
  performance measurement.

## Comparison and restoration

| Runner | Result | Queue/total | Assigned job runtime |
| --- | --- | ---: | ---: |
| `ubuntu-latest` | Passed | 16 seconds total | 8 seconds |
| `blacksmith-2vcpu-ubuntu-2404` | No runner assigned; cancelled | 6m 16s queued | Not started |

The Blacksmith run did not pass, so the conditional restoration and verification
were not performed. The repository currently remains on the Blacksmith runner
label so the provisioning issue can be retried without another code change.

No AI features, paid features, payment methods, secrets, variables, or extra
integrations were enabled.

## Cleanup still required

1. In https://app.blacksmith.sh, verify that **Ocean-by-Mosaic** is fully added
   and that **blacksmith-trial** is visible/enabled. Finish only any required
   runner onboarding step; do not enable optional AI or paid features.
2. Retry **Actions** → **Baseline** → **Run workflow** → **Run workflow**.
3. If the Blacksmith run passes, change the workflow back to
   `runs-on: ubuntu-latest`, push it, and run **Baseline** once more.
4. When testing is finished, uninstall the Blacksmith GitHub App:
   GitHub organization **Settings** → **GitHub Apps** → **Installed GitHub
   Apps** → **Blacksmith** → **Configure** → **Uninstall**.
5. Revoke the Blacksmith OAuth authorization if it is no longer needed:
   GitHub account **Settings** → **Applications** → **Authorized OAuth Apps** →
   **Blacksmith** → **Revoke access**.
6. Delete the disposable repository last:
   repository **Settings** → **General** → **Danger Zone** →
   **Delete this repository**.
