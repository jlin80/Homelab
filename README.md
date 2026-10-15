# Homelab — Infrastructure, Virtualization, and Operations

![Proxmox VE](https://img.shields.io/badge/Virtualization-Proxmox%20VE-E57000?logo=proxmox)
![Linux](https://img.shields.io/badge/Systems-Linux-FCC624?logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Version%20Control-Git-F05032?logo=git&logoColor=white)
![Forgejo](https://img.shields.io/badge/Code%20Hosting-Forgejo-FB923C?logo=forgejo&logoColor=white)

A personal infrastructure lab focused on **virtualization, Linux systems administration, self-hosted services, version control, automation, and operational troubleshooting**. The goal is to practice reliable service operations, controlled changes, and secure infrastructure management.

The live environment is intentionally private. This repository shares the project's technical approach and reusable operational documentation without exposing internal topology or access details.

## Technical focus

- **Virtualization:** operating a personal environment built around Proxmox VE.
- **Linux administration:** maintaining Linux-based systems and troubleshooting service issues.
- **Self-hosted workloads:** running and maintaining private services, including containerized workloads where appropriate.
- **Version control:** tracking project changes with Git and using Forgejo for self-hosted code hosting.
- **Operational discipline:** planning changes, validating outcomes, troubleshooting failures, and documenting recovery steps.
- **Automation:** looking for safe, repeatable ways to reduce manual operational work.
- **Security:** limiting public exposure, protecting credentials, and applying least-privilege principles.

## Portfolio artifacts

- [High-level architecture](docs/architecture-overview.md) — a sanitized conceptual view of the environment and its design principles.
- [Service operations runbook](docs/service-operations-runbook.md) — a reusable template for change validation, troubleshooting, rollback, and incident closeout.

These documents are deliberately generic. They demonstrate operational thinking without publishing private infrastructure details. The runbook is a template, not a claim that every step is already automated or implemented as a formal production process.

## Technologies and tools

**Proxmox VE · Linux · Git · Forgejo · Self-hosted services · Containers · Automation**

This list reflects the tools and areas represented in this project. It does not imply that every component is active at all times or that this repository demonstrates expertise in a cloud provider or a specific CI/CD platform.

## Security boundaries

This public repository intentionally excludes private IP addresses, internal hostnames, node and container inventories, administrative endpoints, access paths, private dashboard screenshots, credentials, and detailed live configurations.

The lab is a learning and operations environment, not a public service. Any future examples should be sanitized, reproducible where practical, and limited to technologies actually used.
