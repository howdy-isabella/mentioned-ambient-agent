# Mentioned

A CamelRun agent that watches for public mentions of CamelAI, camelRun, camelStream, camelBot and camelCode.

The user-facing goal is a daily 9 a.m. Central summary in **#mentioned**, with links, plus checks when asked in Slack. No email. The budget is **$50/month**.

This repository contains the agent's instructions and native CamelRun configuration. There is no custom application server, monitoring runtime, Slack adapter or relay.

## Files

- `agent.yaml`: native CamelRun definition and keyed agent.
- `prompts/mentioned.md`: behavior, watchlist, deduplication and reporting instructions.
- `config/watchlist.json`: the original watchlist and search query suggestions.
- `STATUS.md`: deployment evidence and native product gaps.

The operator handles setup for Isabella. She should not need to create folders, edit configuration files, copy tokens, or use a terminal.

## Native capabilities

Use CamelRun's hosted agent, web search/fetch, durable workspace, native schedules and native Slack integration. Agent-written state files and use of native tools are part of the agent, not a separately maintained application.

Search reservations in the prompt are a conservative instruction, not a hard billing guarantee. The configured $8 agent spend limit is for model usage over the agent's lifetime, not monthly total operating costs. It must not be described as a $50 monthly all-cost cap. No auto top-up or credit purchase is enabled by this project.

## Setup for maintainers

Deploy `agent.yaml` with the official CamelRun CLI, or use the signed-in console's native deployment tools with the same prompt inlined. Keep secrets out of the repository. Use the console's Channels page for Slack setup. Validate a real web search and native Slack round trip before reporting the integration as working.

Native feature gaps are filed in qaml-ai/run; see STATUS.md. Do not work around them with a custom Slack bridge or monitoring service.
