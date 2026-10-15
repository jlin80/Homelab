# Current Homelab State

**Documented:** 2026-10-15  
**Source:** current inventory reported for the Homelab project. This document is not a live health check.

## Reported inventory

| Node | Node IP | CT | Service | Address / notes |
|---|---|---:|---|---|
| PVE | 192.168.100.10 | 100 | Pi-hole | Service address not reconfirmed |
| PVE | 192.168.100.10 | 101 | Vaultwarden | Old references to n8n are obsolete |
| PVE | 192.168.100.10 | 102 | k3s | Cluster status not reconfirmed |
| PVE2 | 192.168.100.11 | 104 | Streaming | IP and ports pending confirmation |
| PVE2 | 192.168.100.11 | 201 | ownCloud Infinite Scale (oCIS) | https://192.168.100.41:9200 |
| PVE2 | 192.168.100.11 | 206 | Database | Engine, IP and ports pending confirmation |
| PVE3 | 192.168.100.12 | 301 | Forgejo | Operational status not verified |
| PVE3 | 192.168.100.12 | 303 | Hermes | Operational status not verified |

## PVE3 incident

PVE3 was reported unreachable over SSH and did not come back after power was disconnected and reconnected. Recovery has not been confirmed. Do not assume Forgejo or Hermes is available until the host and its containers are checked.

## Hermes roles

| Role | Scope |
|---|---|
| Sniper | Focused opportunity discovery and selection |
| Trading | Trading analysis and actions within explicitly authorized limits |
| Watchdog / Alerts | Condition detection and alerting |
| NOC | Infrastructure operations and troubleshooting |
| Developer | Development and project review |
| Research | Research and synthesis |

These are documented roles, not proof that each agent is currently running or has a particular integration or permission. Verify directly in Hermes when access is restored.

## Known documentation drift

- `terraform/containers.tf` still describes CT101 as n8n, CT103 as monitoring and CT201 as Nextcloud, using the old `192.168.1.0/24` network. This conflicts with the current reported inventory.
- The deployment workflow points to legacy monitoring paths and applies Kubernetes manifests. Those destinations and side effects have not been confirmed against the current setup.
- The `monitoring/` directory contains Prometheus, Grafana, Loki/Promtail, Alertmanager and Homepage configuration, but repository presence does not prove these services are running.
- ZFS/NFS, backup schedules/retention, and the self-hosted GitHub Actions runner must be verified before relying on them.

## Safe reconciliation plan

1. Restore access to PVE3 and verify the health of Forgejo and Hermes.
2. Collect a fresh Proxmox inventory: CT IDs, names, node, IP, state and storage.
3. Verify oCIS access and its actual exposure.
4. Confirm backup jobs and perform a restore test.
5. Compare Terraform state, configuration and real resources. Review a plan for unintended replacements before applying anything.
6. Audit the GitHub Actions runner, credentials and deployment targets.
7. Re-enable automatic deployment only after the workflow is updated and tested against confirmed destinations.

**Do not run `terraform apply` or the legacy deployment workflow as a shortcut for reconciling the inventory.**
