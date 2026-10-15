# Service Operations Runbook (Template)

This is a generic operational template for a self-hosted service. Adapt it to a specific service before using it during an incident. It does not describe private production configuration.

## 1. Before making a change

- [ ] Identify the service owner, purpose, dependencies, and expected behavior.
- [ ] Confirm the maintenance scope and potential user impact.
- [ ] Verify that a recent backup exists for data that could be affected.
- [ ] Record the current version and the last known-good configuration.
- [ ] Review the proposed change and ensure that secrets are not stored in source control.
- [ ] Define a validation check and a rollback condition before deployment.

## 2. Apply a change

1. Make one bounded change at a time.
2. Keep configuration and deployment changes version-controlled where practical.
3. Use an explicit version or known release rather than an unreviewed floating version.
4. Apply the change using the service's documented deployment method.
5. Record the change, timestamp, and expected result.

## 3. Validate service health

- [ ] Confirm that the workload is running.
- [ ] Check application logs for startup errors or repeated failures.
- [ ] Test the expected service behavior from an authorized location.
- [ ] Confirm that dependent services remain healthy.
- [ ] Check for unexpected resource consumption or repeated restarts.
- [ ] Record the observed result and any follow-up work.

A running process alone is not sufficient evidence that an application is functioning correctly. Validate the behavior that matters to its users or dependent systems.

## 4. Troubleshoot an incident

1. **Scope:** establish what failed, when it started, and what changed recently.
2. **Contain:** avoid risky repeated restarts or unrelated changes; limit impact where possible.
3. **Inspect:** review service status, relevant logs, dependencies, available resources, and recent configuration changes.
4. **Hypothesize:** identify the most likely cause and choose a test that can distinguish it from alternatives.
5. **Change carefully:** make one reversible change at a time.
6. **Validate:** confirm service behavior and check for regressions.
7. **Document:** record impact, timeline, root cause if known, remediation, and preventive actions.

Do not include passwords, tokens, private keys, internal addresses, or sensitive log excerpts in public incident notes.

## 5. Rollback criteria and procedure

Consider rollback when the change causes a material regression, the validation check fails, or service health cannot be restored within the agreed maintenance window.

- Stop additional changes while the cause is assessed.
- Restore the last known-good version or configuration using the service's established recovery method.
- Restore data from backup only when necessary and after assessing data-loss implications.
- Re-run the validation checks.
- Document the rollback and identify what must change before attempting the deployment again.

## 6. Closeout

- [ ] Service behavior is verified.
- [ ] Monitoring or manual checks show no immediate recurrence.
- [ ] Change and incident notes are updated.
- [ ] Follow-up actions have an owner.
- [ ] Any temporary access or troubleshooting changes are removed.

## Example change record

| Field | Record |
|---|---|
| Service | `<service-name>` |
| Change | `<what changed>` |
| Reason | `<why it changed>` |
| Validation | `<test and expected result>` |
| Rollback trigger | `<condition that requires rollback>` |
| Outcome | `<success, rollback, or follow-up required>` |

This template is a portfolio artifact and should not be presented as evidence that a specific production process is already implemented.
