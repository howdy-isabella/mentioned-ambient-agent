# Mentioned

A CamelRun agent that watches for public mentions of CamelAI, camelRun, camelStream, camelBot and camelCode.

The user-facing goal is a daily 9 a.m. Central summary in **#mentioned**, with links, plus checks when asked in Slack. No email. The budget is **$50/month**.

This repository contains the agent's instructions and native CamelRun configuration. There is no custom application server, monitoring runtime, Slack adapter or relay.

## Files

- `agent.yaml`: native CamelRun definition and keyed agent.
- `prompts/mentioned.md`: behavior, watchlist, deduplication and reporting instructions.
- `config/watchlist.json`: the original watchlist and search query suggestions.
- `config/slack-digest.openapi.json`: native hosted tool definition for posting a digest to the fixed #mentioned channel.
- `assets/mentioned-newspaper.png`: the newspaper emoji image uploaded as the Slack app icon.
- `STATUS.md`: deployment evidence and native product gaps.

The operator handles setup for Isabella. She should not need to create folders, edit configuration files, copy tokens, or use a terminal.

## Native capabilities

Use CamelRun's hosted agent, web search/fetch, shared native volume, native schedules and native Slack integration. Cloudflare's official MCP provides read-only aggregate referral analytics. A native OpenAPI source posts scheduled digests to the fixed #mentioned channel; native Slack channels receive and answer requests. These are tool configurations hosted by CamelRun. There is no custom running process.

Search reservations in the prompt are a conservative instruction, not a hard billing guarantee. The configured $8 agent spend limit is for model usage over the agent's lifetime, not monthly total operating costs. It must not be described as a $50 monthly all-cost cap. No auto top-up or credit purchase is enabled by this project.

Per-request search counts, response-round/time/context overrides and output-token overrides have been removed at the owner's request. Platform/provider ceilings and existing financial safeguards still apply. Research requests in native Slack conversations get an immediate acknowledgment through the native `send_message` tool, followed by the automatic final reply. Background scans stay quiet.

## Setup for maintainers

Deploy `agent.yaml` with the official CamelRun CLI. Its Cloudflare and Slack credential variables must come from a secure environment, never the repository or conversation. The signed-in console can save these native tool sources with credentials sealed. When updating existing sources without changing their destination, omit auth/headers to preserve stored credentials. A redacted `auth: {type: bearer}` response is not a valid deployment credential. Inline the prompt and OpenAPI spec when using native browser deployment tools without secrets.

The native mount in this deployment shares only the original monitor volume's `mentioned` subdirectory at `/monitor`. The central agent and existing Slack DM were explicitly remounted; new Slack conversations inherit it from the definition. Applying a definition updates prompts and tools but does not remount existing agents by itself. Preserve existing state and use `remount: true` for an intentional mount update.

Cloudflare permissions: camelai.com Zone Read and Analytics Read, CamelAI Account Settings Read, and User Details Read required by Cloudflare MCP identity checks. Isabella approved these permissions and storage in CamelRun. The prompt restricts use to aggregate referrals for camelai.com and its subdomains; it excludes visitor identities and raw logs.

Native feature gaps are filed in qaml-ai/run; see STATUS.md. Do not work around them with a custom Slack bridge or monitoring service.
