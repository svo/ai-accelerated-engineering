# Automated Testing

## Overview

Automated test suites are the safety net that enables teams to ship with confidence - but writing, maintaining, and strengthening them is often the most time-consuming part of development. AI accelerates every stage of the automated testing lifecycle: generating tests from code or specifications, identifying and closing coverage gaps, strengthening weak assertions, and maintaining tests as code evolves. This guide draws from testing practices enforced across [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) (pytest with 100% coverage, Hypothesis for property-based testing, mutmut for mutation testing), [**www-qual-is**](https://github.com/svo/www-qual-is) (Vitest for unit tests, Playwright for E2E), with Jest (100% coverage) and OpenAPI/Prism CDCT applied across microservice platforms.

## Approaches

### Test Suite Generation from Existing Code

Point AI at an untested or under-tested module and have it generate a comprehensive test suite. AI analyses the code's branching logic, identifies boundary conditions, and produces tests that cover happy paths, error paths, and edge cases. This is particularly powerful for achieving coverage targets on legacy code where writing tests retroactively is tedious.

### Coverage Gap Analysis and Targeted Test Creation

Use coverage reports as input to AI, which identifies the specific uncovered branches and generates targeted tests to close gaps. Rather than writing tests randomly, AI focuses effort where risk is highest - uncovered error handling, complex conditional logic, and integration boundaries.

### Contract-Driven Test Generation

From an OpenAPI specification or interface definition, AI generates consumer-driven contract tests that verify both sides of a service boundary. This catches integration drift before it reaches production and is especially valuable in microservice architectures where services evolve independently. OpenAPI/Prism CDCT is used across microservice platforms, while [**python-sprint-zero**](https://github.com/svo/python-sprint-zero) includes CDCT scaffolding as part of its template.

### Mutation Testing with AI Analysis

Run mutation testing to find tests that pass regardless of code changes (weak tests), then use AI to analyse the surviving mutants and generate stronger assertions. This moves beyond coverage percentage to actual test effectiveness - a test that never fails is a test that never protects you.

### Continuous Test Maintenance

As code evolves, tests break. AI can analyse test failures, distinguish between genuine regressions and tests that need updating, and propose fixes. This reduces the maintenance burden that often leads teams to delete tests rather than fix them.

## Tooling

| Tool | Purpose |
|------|---------|
| **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** | AI pair programmer for generating tests, analysing coverage gaps, and maintaining test suites |
| **[pytest](https://docs.pytest.org)** | Python testing framework scaffolded with 100% coverage configuration (python-sprint-zero) |
| **[Vitest](https://vitest.dev)** | Frontend unit testing framework ([www-qual-is](https://github.com/svo/www-qual-is)) |
| **[Jest](https://jestjs.io)** | JavaScript testing framework with 100% coverage enforcement (microservice platforms) |
| **[Hypothesis](https://hypothesis.readthedocs.io)** | Python property-based testing for broader input coverage |
| **[mutmut](https://github.com/boxed/mutmut)** | Python mutation testing to evaluate test suite effectiveness |
| **[Playwright](https://playwright.dev)** | End-to-end testing for web applications with visual and interaction testing |
| **[OpenAPI](https://www.openapis.org) / [Prism](https://github.com/stoplightio/prism) CDCT** | Consumer-driven contract testing for microservice integration boundaries |

## Key Questions

- What percentage of your test suite was written after the code, versus driving the design?
- How would 100% coverage with enforced complexity limits change your deployment confidence?
- Where in your codebase would AI-generated tests have the highest return - untested legacy code, or new features?
