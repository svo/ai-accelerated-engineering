# Architecture Governance & Decision-Making

## Overview

Architecture erodes not through grand failures but through a thousand small violations - a domain model that imports a database client, a UI component that calls an API directly, a decision made in Slack and never recorded. AI can serve as both architect's assistant and governance enforcer, generating architectural documentation and continuously validating that the codebase matches its intended design. This guide draws from the [**organisation-template**](https://github.com/svo/organisation-template) (team topologies, RACI/RAPID/RAID decision frameworks, sensible defaults for technology choices), [pytest-archon](https://github.com/jwbargsten/pytest-archon) and [dependency-cruiser](https://github.com/sverweij/dependency-cruiser) enforcement across [**python-sprint-zero**](https://github.com/svo/python-sprint-zero), [**www-qual-is**](https://github.com/svo/www-qual-is), and microservice platforms, and comprehensive static analysis tooling.

## Approaches

### Automated Architectural Boundary Enforcement

Define your architectural rules (hexagonal layers, dependency direction, module boundaries) and enforce them in CI. AI generates the configuration or custom lint rules from a natural language description of your architecture. [**python-sprint-zero**](https://github.com/svo/python-sprint-zero), [**www-qual-is**](https://github.com/svo/www-qual-is), and microservice platforms ship with configurations that enforce hexagonal layer boundaries - domain must not import infrastructure, and violations fail the build. Projects additionally enforce cyclomatic complexity limits and security rules (via e.g. bandit and semgrep).

### Architecture Decision Record Generation

When a technical decision is made, AI can generate a structured ADR capturing the context, decision, consequences, and alternatives considered. Rather than decisions living in Slack threads or meeting notes, they become versioned, searchable artefacts in the repository. Reusable ADR templates provide the framework.

### Technology Radar Maintenance

Track your organisation's technology choices across adopt, trial, assess, and hold categories. AI can analyse your repositories to identify which technologies are actively used, which are being adopted, and which are being phased out - then update the radar accordingly. ThoughtWorks Radar provides a proven visualisation format.

### RACI/RAPID Framework Application

For architectural decisions that span teams, AI can help apply decision frameworks - identifying who is Responsible, Accountable, Consulted, and Informed, or mapping the RAPID roles (Recommend, Agree, Perform, Input, Decide). The [**organisation-template**](https://github.com/svo/organisation-template) provides reusable RACI, RAPID, and RAID frameworks alongside team topology definitions (stream-aligned, platform, enabling, complicated subsystem teams) and cost/incident management processes. This turns governance from a bottleneck into a clear, fast process.

### Codebase Health Metrics

AI can analyse your codebase against DORA metrics (deployment frequency, lead time, change failure rate, recovery time), cyclomatic complexity limits, test coverage thresholds, and dependency health. Python projects enforce this through xenon (cyclomatic complexity), coverage.py (100% coverage threshold), pip-audit (dependency vulnerability scanning), and semgrep (security pattern detection). It generates reports highlighting areas of concern and suggesting specific improvements.

### Architectural Drift Detection

Periodically run AI analysis against your intended architecture to detect drift - new dependencies that violate boundaries, modules that have grown beyond their intended scope, or patterns that have diverged across services. This proactive detection prevents the gradual erosion that makes codebases unmaintainable.

## Tooling

| Tool | Purpose |
|------|---------|
| **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** | AI assistant for generating ADRs, analysing architecture, and suggesting improvements |
| **[pytest-archon](https://github.com/jwbargsten/pytest-archon)** | Validates architectural boundaries in Python projects (e.g., domain must not import infrastructure) |
| **[dependency-cruiser](https://github.com/sverweij/dependency-cruiser)** | Validates architectural boundaries in TypeScript/JavaScript projects |
| **[xenon](https://github.com/rubik/xenon)** | Cyclomatic complexity enforcement for Python codebases |
| **[coverage.py](https://coverage.readthedocs.io)** | Test coverage measurement and threshold enforcement (100% coverage) |
| **[bandit](https://github.com/PyCQA/bandit)** | Security-focused static analysis for Python code |
| **[semgrep](https://semgrep.dev)** | Security pattern detection and custom rule enforcement |
| **[pip-audit](https://github.com/pypa/pip-audit)** | Dependency vulnerability scanning for Python projects |

## Key Questions

- When was the last architectural decision in your project that was formally recorded - and how many have been made informally since?
- What architectural boundaries exist in your codebase today, and are they enforced or aspirational?
- How would continuous architectural validation change the way your team makes technical decisions?
