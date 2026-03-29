# Personal Productivity Agents

## Overview

AI agents that handle the administrative overhead around software development - summarising what happened overnight, surfacing action items, and managing the communication burden so developers can stay focused. This guide covers how to build personal agents that integrate with the tools developers already use, turning reactive notification-checking into proactive, prioritised briefings. The [**hermes**](https://github.com/svo/hermes) project demonstrates this: a personal productivity agent using OpenClaw, integrating with Google Suite (Gmail, Calendar, Drive via gog CLI) and Slack, with a Telegram interface for conversational task delegation - deployed as a Docker container with scheduled briefing runs.

## Approaches

### Development Activity Briefings

An AI agent monitors your repositories, CI/CD pipelines, and issue trackers overnight and delivers a structured morning briefing - pull requests awaiting your review, failed builds, deployment status, and issues assigned to you. [**hermes**](https://github.com/svo/hermes) provides morning briefings via Telegram, synthesising activity from Gmail, Google Calendar, and development platforms into a single prioritised summary. This replaces the first 30 minutes of scattered tab-checking with a single actionable message.

### Notification Triage and Prioritisation

Developers are bombarded with notifications across email, chat, issue trackers, and code review tools. An AI agent can triage these by urgency and relevance - surfacing blocking PR comments, build failures, and production alerts while batching lower-priority items for later. You start the day knowing what matters, not drowning in noise.

### Context Preparation for Meetings

Before a standup, sprint review, or architecture discussion, an AI agent can prepare briefing notes - summarising recent commits, open PRs, and unresolved issues relevant to the agenda. This turns meeting prep from a manual exercise into an automated deliverable.

### Cross-Platform Information Synthesis

Developers operate across code review tools, chat, issue trackers, documentation, and CI dashboards. An AI agent that spans these platforms can answer questions like "What was decided about the API redesign last week?" by synthesising across sources.

### Focus Time Protection

Configure the agent to respect deep work - batching notifications, holding non-urgent items, and only interrupting for genuine emergencies like production incidents or blocking reviews. This turns the agent from another notification source into an attention guardian.

### Conversational Task Delegation

Interact with your agent via natural language through chat. "Remind me to follow up on that PR tomorrow" or "What's the status of the deployment?" - the agent handles the lookup or scheduling while you stay in your editor. [**hermes**](https://github.com/svo/hermes) supports this through Telegram and Slack integrations, using gog to read and manage Gmail, Calendar, and Drive on your behalf.

## Tooling

| Tool | Purpose |
|------|---------|
| **[OpenClaw](https://github.com/openclaw/openclaw)** | Python agent framework for building productivity agents with tool integration and scheduling |
| **[Claude API](https://docs.anthropic.com/en/docs/api-reference) / [OpenAI API](https://platform.openai.com/docs/api-reference)** | LLM backbone for summarisation, triage logic, and natural language interaction |
| **[gog](https://github.com/steipete/gogcli) (Google Suite CLI)** | Access to Gmail, Google Calendar, and Google Drive for email/calendar/contact management |
| **[GitHub API](https://docs.github.com/en/rest)** | Access to pull requests, commits, reviews, and repository activity |
| **[Telegram Bot API](https://core.telegram.org/bots/api)** | Conversational interface for agent interaction, briefing delivery, and task delegation |
| **[Slack Webhooks](https://api.slack.com/messaging/webhooks)** | Team-facing distribution for notifications and alerts |
| **Cron / systemd timers** | Scheduling briefings, triage runs, and periodic check-ins |
| **[Docker](https://www.docker.com)** | Containerised deployment for the agent with persistent state |

## Key Questions

- How much time do you spend each morning catching up on what happened overnight across your tools?
- What information would you want in a daily developer briefing?
- Where is the line between helpful automation and losing touch with important context?
