# Exploratory Testing

## Overview

Exploratory testing is a discovery discipline - the tester simultaneously learns about the system, designs tests, and executes them, guided by curiosity and evolving hypotheses. AI transforms this practice by bringing tireless pattern recognition, broader coverage, and systematic documentation to what has traditionally been an entirely manual, expertise-dependent activity. This guide focuses on using agents to explore applications and find what nobody thought to look for. The [**exploratory-tester**](https://github.com/svo/exploratory-tester) project provides a toolkit: a system using Claude Code with Playwright MCP for AI-driven browser automation, packaged as a multi-arch Docker image.

## Approaches

### Hypothesis-Driven Exploration

An AI agent interacts with your application the way an exploratory tester would - observing behaviour, forming hypotheses about what might break, and designing experiments to test them. The [**exploratory-tester**](https://github.com/svo/exploratory-tester) uses Claude Code's reasoning capabilities to form and test hypotheses, while Playwright MCP gives it hands-on browser control to navigate, interact, and observe. Unlike scripted tests that verify known expectations, exploratory testing discovers unknowns. AI brings speed and breadth to this process without losing the curiosity that makes it effective.

### Session-Based Exploration with AI

Structure AI exploration using session-based test management (SBTM). Define a charter - "Explore the payment flow under unusual input combinations" - and let the AI execute a time-boxed session, documenting observations, bugs found, and areas requiring further investigation. Each session produces a structured report that feeds into the next.

### Cross-Flow and Cross-Role Testing

AI can systematically explore how different user roles interact with the same features, testing permission boundaries, data visibility, and workflow handoffs. It can switch between roles mid-session, testing scenarios like "what happens when a user with role A sees data created by role B?" - combinations that are tedious to test manually.

### State Space Exploration

Applications have vast state spaces that manual testing barely scratches. AI can systematically vary inputs, sequences, timing, and environmental conditions to explore states. It identifies unusual state combinations - partial form submissions, interrupted workflows, concurrent operations - and documents which ones produce unexpected behaviour.

### Visual and Layout Regression Discovery

AI can navigate through application screens, identify visual anomalies, layout breaks, and accessibility issues that functional tests miss. By comparing current rendering against expected patterns, it catches regressions that only a human eye would typically notice.

### Risk-Based Exploration Prioritisation

Feed AI information about recent code changes, known fragile areas, or upcoming releases, and it prioritises its exploration accordingly. Changed code gets more attention; stable, well-tested areas get less. This focuses discovery effort where the risk is highest.

## Tooling

| Tool | Purpose |
|------|---------|
| **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** | AI agent driving the exploratory testing session with reasoning and documentation |
| **[Playwright MCP](https://github.com/microsoft/playwright-mcp)** | Browser automation giving the AI hands-on control of web applications |
| **[Docker](https://www.docker.com) (multi-arch)** | Containerised deployment of the exploratory testing toolkit |
| **[Vagrant](https://www.vagrantup.com) / [Ansible](https://www.ansible.com) / [Packer](https://www.packer.io)** | Environment provisioning for reproducible testing infrastructure |
| **[mitmproxy](https://mitmproxy.org)** | Network traffic inspection for observing API calls during exploration |

## Key Questions

- What parts of your application have never been explored by a tester - only verified by scripted tests?
- How would you structure an AI exploration charter for the most risk-prone area of your system?
- What would change if every release included an AI-driven exploratory session alongside your automated suite?
