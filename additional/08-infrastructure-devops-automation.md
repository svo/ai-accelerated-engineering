# Infrastructure & DevOps Automation

## Overview

Infrastructure-as-code is inherently declarative and pattern-heavy. AI can produce production-grade infrastructure configurations that would otherwise require deep platform expertise and hours of documentation reading. This guide covers how to compress the gap between "I need a deployment" and "it's running in production" - tools and patterns for infrastructure provisioning, configuration management, containerisation, and environment reproducibility - using Terraform, Terragrunt, Ansible, Packer, Vagrant, and Docker.

## Approaches

### Infrastructure Provisioning from Requirements

Describe your infrastructure needs in plain language - "I need a database with a composite key, a managed auth service with email verification, and an email domain for transactional messages" - and AI generates the corresponding Terraform modules with sensible defaults, proper access policies, and output values. Reusable modules for databases, managed auth services, and email infrastructure can be wrapped with Terragrunt for environment-specific configuration. The developer focuses on what they need, not the syntax of the provisioning tool.

### Multi-Environment Configuration

Most projects need at least development, staging, and production environments. AI generates the Terragrunt configuration wrappers that manage environment-specific variables, remote state, and dependency ordering across modules. Shared configuration and per-environment directories with Terragrunt - including two-phase deployment patterns (resource creation first, then dependent service enablement) - turn a single-environment setup into a full pipeline without manual duplication.

### Configuration Management and Server Provisioning

From a description of the desired server state, AI generates idempotent Ansible playbooks with proper handlers and role-based organisation. [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) includes Ansible roles for server provisioning, while [**my-debian-setup**](https://github.com/svo/my-debian-setup) and [**my-macos-setup**](https://github.com/svo/my-macos-setup) apply the same pattern to developer workstation configuration. This pattern works equally well for developer workstation setup and production server configuration - reproducible environments from a single command.

### Container Build Optimisation

AI generates multi-stage Dockerfiles optimised for both development (fast rebuilds, debugging tools) and production (minimal image, security scanning). [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) demonstrates this with multi-stage Docker builds, Packer creating machine images from Ansible roles, and multi-arch support via GitHub Actions.

### CI/CD Pipeline Generation

Describe your deployment workflow and AI generates the pipeline configuration for your platform of choice. It includes test stages, security scanning, deployment gates, and rollback procedures appropriate to your risk tolerance. As requirements change, AI updates the pipeline rather than requiring manual YAML editing.

### Environment Reproducibility

AI generates Vagrant + Ansible development environment configurations that create identical setups for every team member. [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) ships with a Vagrantfile and Ansible provisioning that creates a fully configured development environment from a single `vagrant up` command. This ensures "works on my machine" is a solved problem - new team members are productive from their first day.

## Tooling

| Tool | Purpose |
|------|---------|
| **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** | Generating and debugging infrastructure code from natural language requirements |
| **[Terraform](https://www.terraform.io)** | Declarative AWS resource provisioning with reusable modules |
| **[Terragrunt](https://terragrunt.gruntwork.io)** | Environment-specific Terraform configuration wrappers with remote state management |
| **[Ansible](https://www.ansible.com)** | Server and workstation provisioning with idempotent, role-based playbooks |
| **[Packer](https://www.packer.io)** | Machine image creation from Ansible roles for cloud deployment |
| **[Docker](https://www.docker.com)** | Multi-stage, multi-architecture container image creation |
| **[Vagrant](https://www.vagrantup.com)** | Reproducible development environments for consistent team onboarding |
| **[GitHub Actions](https://github.com/features/actions)** | CI/CD pipeline automation with test stages, security scanning, and deployment gates |

## Key Questions

- How long does it take a new team member to get a working development environment today?
- Which infrastructure configurations in your project are manually maintained that could be generated?
- What would change if every developer could confidently modify infrastructure code with AI assistance?
