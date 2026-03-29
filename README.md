# AI-Accelerated Engineering

Practical guides for software engineers and teams looking to become more productive through AI tooling and approaches. Each topic covers actionable techniques, recommended tools, and real-world examples.

---

## 1. [Autonomous Research & Content Generation](additional/01-autonomous-research-content-generation.md)

AI agents that autonomously research topics, synthesise findings from multiple sources, and produce structured output - whether reports, summaries, or publishable content. Demonstrated through [**aletheia**](https://github.com/svo/aletheia) (philosophy of technology research agent) and [**rosa**](https://github.com/svo/rosa) (AI adoption and enterprise trends research agent) - both agents using OpenClaw, Brave Search, and Firecrawl, deployed via Docker with cron-scheduled research pipelines.

**Example use cases:**
- Automate competitive analysis, market research, or technology trend monitoring on a recurring schedule
- Generate draft documentation, release notes, or internal briefings from source material
- Stay current on regulatory changes, industry standards, or emerging tools relevant to your project

---

## 2. [Sprint Zero & Project Scaffolding](additional/02-sprint-zero-project-scaffolding.md)

A consistent architectural pattern (hexagonal architecture + DDD) replicated across services with 100% test coverage, dependency injection, OpenAPI, and infrastructure-as-code baked in. Demonstrated through [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) (FastAPI, pytest, Lagom) as the primary microservice template, [**typescript-sprint-zero**](https://github.com/svo/typescript-sprint-zero) (Node.js, Vitest, tsyringe) as the TypeScript counterpart, and [**www-qual-is**](https://github.com/svo/www-qual-is) (Next.js 15, React 19, Tailwind CSS) for web application scaffolding. Applied at scale across multi-service platforms.

**Example use cases:**
- Scaffold new services or modules with consistent architecture, tests, and deployment configuration already in place
- Generate dependency injection bindings, API route registrations, and test fixtures for a new domain module by describing its purpose and boundaries
- Maintain consistency across multiple services by using the template as a reference when AI detects pattern drift in existing codebases

---

## 3. [Legacy Code Modernisation](additional/03-legacy-code-modernisation.md)

Specialised AI skills codifying proven refactoring techniques. Demonstrated through [**claude-working-effectively-with-legacy-code**](https://github.com/svo/claude-working-effectively-with-legacy-code) - a drop-in Claude Code configuration with 11 reusable skills: codebase-assessment, legacy-code-change, characterisation-test, seam-finder, dependency-breaker, sprout-method, wrap-and-decorate, scratch-refactor, effect-analysis, strangler-fig, and branch-by-abstraction.

**Example use cases:**
- Generate characterisation tests for unfamiliar code before making changes
- Identify seams and safe intervention points when working with tightly coupled modules
- Apply strangler fig or branch-by-abstraction patterns to incrementally replace legacy components without big-bang rewrites

---

## 4. [Exploratory Testing](additional/04-exploratory-testing.md)

AI agents that interact with applications the way a curious, methodical human tester would - forming hypotheses about what might break, navigating unexpected states, and documenting findings. Demonstrated through [**exploratory-tester**](https://github.com/svo/exploratory-tester) - a toolkit using Claude Code and Playwright MCP for AI-driven browser exploration, deployed via multi-arch Docker images with Vagrant/Ansible/Packer for environment provisioning.

**Example use cases:**
- Run AI-driven exploration sessions against new features before release to find what scripted tests miss
- Test cross-role and cross-flow interactions that are tedious to verify manually
- Use session charters to focus exploration on recently changed or high-risk areas of the application

---

## 5. [Automated Testing](additional/05-automated-testing.md)

Using AI to generate, maintain, and strengthen test suites - from unit tests and contract tests to coverage gap analysis and mutation testing. Demonstrated across [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) (pytest, coverage.py, Hypothesis, mutmut - enforcing 100% coverage) and [**www-qual-is**](https://github.com/svo/www-qual-is) (Vitest, Playwright E2E), with Jest (100% coverage) and OpenAPI/Prism CDCT applied across microservice platforms.

**Example use cases:**
- Generate unit and integration tests for existing code that lacks coverage
- Feed coverage reports to AI and have it produce targeted tests for uncovered branches
- Use mutation testing results to identify weak assertions and strengthen them with AI assistance

---

## 6. [Personal Productivity Agents](additional/06-personal-productivity-agents.md)

AI agents that handle the administrative overhead around software development - summarising what happened overnight, surfacing action items, and managing the communication burden so developers can stay focused. Demonstrated through [**hermes**](https://github.com/svo/hermes) - a personal productivity agent using OpenClaw, integrating with Google Suite (Gmail, Calendar, Drive via gog) and Slack, with a Telegram interface for conversational task delegation.

**Example use cases:**
- Receive a morning briefing summarising pull request activity, CI/CD failures, and messages requiring your attention
- Automatically triage notifications across email, chat, and issue trackers so you start the day with priorities, not noise
- Delegate routine communication (meeting scheduling, status update replies, follow-up reminders) to an agent via chat

---

## 7. [Full-Stack Product Development](additional/07-fullstack-product-development.md)

An orchestrating agent that holds the macro context of the entire product - architecture, service boundaries, data contracts - and generates targeted prompts for specialist agents that work on individual components. Demonstrated through multi-service platforms built with Python microservices (FastAPI, Lagom, hexagonal architecture) and Next.js 15/React 19 frontends - coordinating changes across multiple backend services and frontends simultaneously.

**Example use cases:**
- Use an orchestrating agent to decompose a feature into coordinated changes across frontend and backend services, then delegate each to a focused agent
- Keep API contracts, shared types, and cross-service patterns consistent by having the orchestrator review and align the output of component-level agents
- Spin up a specialist agent per service or module, each scoped to its own codebase, while the orchestrator manages dependencies between them

---

## 8. [Infrastructure & DevOps Automation](additional/08-infrastructure-devops-automation.md)

Using AI to generate and maintain infrastructure-as-code, container configurations, provisioning scripts, and CI/CD pipelines. Demonstrated through **infrastructure-as-code** (Terraform + Terragrunt for AWS with reusable modules) and the IaC layer of [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) (Vagrant, Ansible, Packer, Docker - reproducible environments from dev to production).

**Example use cases:**
- Describe infrastructure needs in plain language and generate the corresponding provisioning code, container definitions, and deployment configurations
- Create reproducible development environments so new team members are productive from day one
- Generate and maintain CI/CD pipelines with appropriate test stages, security scanning, and deployment gates

---

## 9. [Architecture Governance & Decision-Making](additional/09-architecture-governance.md)

Architecture Decision Records, architectural boundary enforcement via static analysis, RACI/RAPID frameworks, tech radar, and DORA metrics templates. Outlined in [**organisation-template**](https://github.com/svo/organisation-template) (team topologies, RACI/RAPID/RAID frameworks, sensible defaults), with enforcement across [**python-sprint-zero**](https://github.com/svo/python-sprint-zero), [**www-qual-is**](https://github.com/svo/www-qual-is), and microservice platforms using static analysis tooling.

**Example use cases:**
- Generate Architecture Decision Records when technical decisions are made, capturing context, alternatives, and consequences
- Enforce architectural boundaries (e.g., hexagonal layer rules) automatically in CI via AI-generated configurations
- Detect pattern drift by comparing service implementations against established templates and architectural conventions

