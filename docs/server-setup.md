erver Setup Documentation

## Document Information

| Item | Value |
|------|-------|
| Project | TaskFlow DevOps Platform |
| Environment | Development |
| Operating System | Ubuntu Server 24.04 LTS |
| Document Version | 1.0 |
| Prepared By | <Your Name> |
| Date | <DD-MM-YYYY> |

---

# Purpose

This document describes the initial server configuration performed before deploying the TaskFlow DevOps Platform. The objective is to prepare a secure and standardized Ubuntu Server that will be used for application deployment, automation, and future CI/CD integration.

---

# Server Information

| Property | Value |
|----------|-------|
| Hostname | <Output of `hostname`> |
| Ubuntu Version | Ubuntu Server 24.04 LTS |
| Kernel Version | <Output of `uname -r`> |
| Architecture | x86_64 |
| Deployment Directory | /opt/taskflow |
| Development Repository | ~/Projects/taskflow-devops |

---

# Deployment User

A dedicated deployment user has been created for automated application deployments.

| Property | Value |
|----------|-------|
| Username | deploy |
| Home Directory | /home/deploy |
| Purpose | CI/CD Deployments |
| Sudo Access | Yes |
| Docker Group | Will be added after Docker installation |

Why a dedicated deployment user?

- Avoid deploying applications using a personal user account.
- Separate deployment responsibilities from administrator activities.
- Improve security and auditability.
- Follow production best practices.

---

# Firewall Configuration

Firewall management is performed using **UFW (Uncomplicated Firewall)**.

Current configuration:

| Service | Status |
|----------|--------|
| UFW | Enabled |
| SSH (22/TCP) | Allowed |

Verification Commands

```bash
sudo ufw status
```

```bash
sudo ufw status numbered
```

---

# Project Directory Structure

Deployment directory:

```
/opt/taskflow
├── backups/
├── logs/
├── releases/
└── shared/
```

Purpose of each directory:

| Directory | Description |
|-----------|-------------|
| releases | Stores application releases deployed by the CI/CD pipeline. |
| shared | Stores persistent data shared across releases. |
| backups | Stores database and application backups. |
| logs | Stores deployment and application logs. |

---

# Development Repository Structure

Source code is maintained separately from deployment files.

```
~/Projects/taskflow-devops
```

This repository contains:

- Docker configuration
- GitHub Actions workflows
- Terraform configuration
- Ansible playbooks
- Monitoring configuration
- Documentation

---

# Installed Packages

The following utilities have been installed during the initial server setup:

- Git
- Curl
- Wget
- Vim
- Nano
- Tree
- Net-tools
- ZIP / Unzip
- JQ
- CA Certificates
- Software Properties Common

These tools are required for system administration and future deployment automation.

---

# SSH Configuration

SSH service is enabled for remote administration.

Authentication method:

- Password Authentication (Current)
- SSH Key Authentication (To be configured in the next phase)

Future work:

- Disable password authentication
- Enable SSH key-only authentication
- Restrict root login

---

# Next Steps

The following tasks will be completed in the next sprint:

- Install Docker Engine
- Install Docker Compose
- Configure Docker permissions
- Deploy OpenProject
- Configure Docker networking
- Prepare GitHub Actions for automated deployments

---

# Verification Commands

```bash
hostnamectl
```

```bash
hostname
```

```bash
lsb_release -a
```

```bash
uname -r
```

```bash
df -h
```

```bash
free -h
```

```bash
hostname -I
```

```bash
sudo ufw status
```

---

# Summary

The Ubuntu Server has been prepared as the deployment environment for the TaskFlow DevOps Platform. A dedicated deployment user has been created, the firewall has been configured, and the required directory structure has been established. The server is now ready for Docker installation and the implementation of an automated CI/CD pipeline.
