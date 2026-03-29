# Legacy Code Modernisation

## Overview

Legacy code is the silent majority of most codebases - working software that nobody dares change because nobody fully understands it. AI transforms legacy modernisation from a high-risk, high-cost endeavour into an incremental, confidence-building process. This guide explores how proven refactoring techniques can be codified as executable AI skills, creating a practical toolkit for safely transforming legacy codebases. The entire approach is packaged as [**claude-working-effectively-with-legacy-code**](https://github.com/svo/claude-working-effectively-with-legacy-code) - a drop-in Claude Code configuration (`.claude/CLAUDE.md` + 11 reusable skills) that can be added to any repository to enable AI-assisted legacy modernisation.

## Approaches

### Characterisation Testing

Before changing legacy code, establish what it actually does. AI can analyse existing code paths, generate characterisation tests that capture current behaviour (including edge cases), and build a safety net that makes refactoring possible. This is the essential first step - you cannot safely change what you cannot verify. The **characterisation-test** skill in claude-working-effectively-with-legacy-code automates this process, while the **codebase-assessment** skill provides an initial survey of the codebase's structure and risk areas.

### Seam Identification

A seam is a place where you can alter behaviour without editing the code at that point. AI excels at scanning codebases for natural seams - interfaces, configuration points, dependency injection sites, and polymorphic call sites. The **seam-finder** skill automates this analysis, producing a map of safe intervention points.

### Safe Legacy Code Changes

When you need to make a change to legacy code, AI can guide the process - identifying the safest intervention point, suggesting which techniques to apply, and generating the tests needed to proceed with confidence. The **legacy-code-change** skill orchestrates this workflow, combining seam analysis, characterisation testing, and targeted refactoring into a structured change process.

### Strangler Fig Pattern

Incrementally replace legacy components by routing new functionality through modern implementations while the old code continues to serve existing traffic. The **strangler-fig** skill identifies extraction boundaries, generates the new implementation alongside the old, and creates the routing logic that gradually shifts traffic.

### Branch by Abstraction

Introduce an abstraction layer over legacy code, build a new implementation behind that abstraction, and switch over when ready. The **branch-by-abstraction** skill accelerates this by generating the abstraction interface from the legacy code's actual usage patterns, then scaffolding the new implementation with tests already in place.

### Dependency Breaking Techniques

Legacy code often resists testing because of tight coupling. The **dependency-breaker** skill identifies problematic dependencies and applies targeted techniques: extract interface, parameterise constructor, introduce static setter, or adapt parameter. Additional skills - **sprout-method**, **wrap-and-decorate**, and **scratch-refactor** - provide complementary approaches for safely introducing new behaviour alongside legacy code, while **effect-analysis** maps the ripple effects of proposed changes before they are made.

### Incremental Architecture Migration

Move from a tangled architecture to hexagonal/clean architecture one module at a time. AI identifies which modules have the fewest inbound dependencies (safest to extract first), generates the ports and adapters, and validates that architectural boundaries hold after each step.

## Tooling

| Tool | Purpose |
|------|---------|
| **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** | AI pair programmer with custom skills for legacy refactoring patterns |

## Key Questions

- Which parts of your codebase does the team avoid changing - and what would it take to make them safe to touch?
- Have you attempted a legacy rewrite that failed? What went wrong?
- How would characterisation testing change your confidence in making changes to unfamiliar code?
