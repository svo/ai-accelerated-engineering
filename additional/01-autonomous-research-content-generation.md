# Autonomous Research & Content Generation

## Overview

AI agents can operate as always-on research assistants - scanning the web for emerging trends, synthesising findings, and producing publishable content on a schedule. This guide covers how to build, configure, and deploy autonomous research agents that turn curiosity into structured output without manual intervention. Two production examples demonstrate the approach: [**aletheia**](https://github.com/svo/aletheia) - an agent researching the intersection of philosophy and technology, and [**rosa**](https://github.com/svo/rosa) - an agent analysing AI adoption trends in enterprise and SaaS. Both use OpenClaw as the agent framework with Brave Search and Firecrawl for information gathering, creating blog drafts and distributing using Telegram on cron-scheduled cadences.

## Approaches

### Scheduled Research Pipelines

Define a research brief (topic, tone, philosophical lens, audience) and let an agent execute it on a recurring cadence. The agent searches the web, reads source material, synthesises findings, and outputs a formatted blog post or briefing. Each agent can be configured with a distinct personality and domain focus, running on a daily or weekly schedule via cron. [**aletheia**](https://github.com/svo/aletheia) operates at the intersection of philosophy and technology with a defined philosophical lens, while [**rosa**](https://github.com/svo/rosa) focuses on AI adoption with a warm, service-design-oriented tone - both running autonomously as Docker containers with scheduled pipelines.

### Multi-Source Information Gathering

Combine web search APIs with deep page fetching to move beyond surface-level results. An agent can issue a broad search query, identify the most promising sources, then fetch and parse full articles for richer synthesis. This two-pass approach (search then fetch) produces higher-quality output than single-query summarisation.

### Multi-Channel Distribution

Route agent output to where it is most useful. A single research run can publish a blog post to a CMS, send a summary to a Telegram channel, and post highlights to Slack - ensuring the right audience sees the work without manual cross-posting. Both [**aletheia**](https://github.com/svo/aletheia) and [**rosa**](https://github.com/svo/rosa) distribute content across multiple channels from a single research run: blog posts via markdown with frontmatter (ingested by [**www-qual-is**](https://github.com/svo/www-qual-is)), summaries to Telegram, and highlights to Slack.

### Personality and Tone Configuration

Define the agent's voice, philosophical framework, and editorial standards in its system prompt. This turns a generic LLM into a domain-specific researcher with consistent output quality. [**aletheia**](https://github.com/svo/aletheia) operates at the intersection of philosophy and technology with a critical, analytical lens, while [**rosa**](https://github.com/svo/rosa) focuses on service design with a warm, empathetic tone - each configured entirely through their OpenClaw agent definition.

### Guardrails and Review Loops

Introduce human-in-the-loop review for sensitive topics or high-stakes publications. Agents can draft to a staging channel for approval before final publication, or flag low-confidence outputs for manual review.

## Tooling

| Tool | Purpose |
|------|---------|
| **[OpenClaw](https://github.com/openclaw/openclaw)** | Python agent framework for defining research agents with configurable tools, personality, and scheduling (used by aletheia, rosa) |
| **[Claude API](https://docs.anthropic.com/en/docs/api-reference) / [OpenAI API](https://platform.openai.com/docs/api-reference)** | LLM backbone for synthesis, summarisation, and content generation |
| **[Brave Search API](https://brave.com/search/api/)** | Web search integration for discovering current sources and trends |
| **[Firecrawl](https://github.com/mendableai/firecrawl)** | Deep web page fetching and parsing for full-text extraction from discovered URLs |
| **[Telegram Bot API](https://core.telegram.org/bots/api)** | Distribution channel for delivering agent output to mobile/desktop (aletheia, rosa) |
| **[Slack Webhooks](https://api.slack.com/messaging/webhooks)** | Team-facing distribution for research summaries and alerts |
| **Cron / systemd timers** | Scheduling agent runs on daily, weekly, or custom cadences |
| **[Docker](https://www.docker.com)** | Containerised deployment for reproducible, isolated agent environments |
| **[Markdown](https://commonmark.org) / [gray-matter](https://github.com/jonschlinkert/gray-matter)** | Structured content output with frontmatter metadata for ingestion by [www-qual-is](https://github.com/svo/www-qual-is) (Next.js) |

## Key Questions

- What research tasks in your current work are repetitive enough to automate?
- How do you balance agent autonomy with editorial quality control?
- What distribution channels would give your team the most value from automated research?
