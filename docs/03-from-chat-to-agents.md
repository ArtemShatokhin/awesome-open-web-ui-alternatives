# From chat to agents: moving a team to Kortix, the open-source AI Operating System

Kortix is the open-source AI Operating System. A team on Open WebUI has a self-hosted, open-source chat window over its models and documents, and that covers a lot of ground. The pressure to change tools arrives at a specific moment: when the answer has to leave the chat and become a change in a real system, and nobody can say which machine ran it or who signed off. This note is about that moment. The [Open WebUI for teams page](https://openwebuialternative.com/open-webui-for-teams) covers the same decision for a general audience.

## What a chat window is good at

Open WebUI is built for the interface. You install it with Docker or pip, connect Ollama and any OpenAI-compatible API, and a team gets a chat over its models and documents, with plugins, retrieval and per-user groups around it ([Open WebUI repository](https://github.com/open-webui/open-webui)). The project has moved toward execution: Open Terminal gives an agent a terminal and a filesystem inside the chat, and Terminals gives each user an isolated environment ([Open WebUI repository](https://github.com/open-webui/open-webui)). The center of gravity stays the conversation, where a person drives every turn and the output is a reply.

## The session replaces the turn

In Kortix the unit of work is a session, and each session runs an agent on its own isolated sandbox and its own branch. One isolated sandbox per session, and each session has its own isolated machine and branch, so the agent can install, run and break anything on that machine while only what it commits survives ([Kortix on GitHub](https://github.com/kortix-ai/suna)). The harness that turns a model into an agent is OpenCode, configured by a file in the repo, so an agent's planning and tool use are readable. Thousands of agents run in parallel on one config, each on its own cloud computer.

## A person reviews before it lands

Session work reaches `main` through a change request. Merge is default-deny for agents, so nothing an agent produces goes live until a person reads the diff and approves it. An agent can edit its own configuration on its session branch and propose the change, and a person approves it. Approval gates you set, off until you set them. The effect on a team is that the repo improves one reviewed change at a time, and each change is a diff a manager can read.

## Work starts without anyone watching

A trigger starts a session on a cron schedule or a signed webhook, with nobody present. Ways work runs: on demand, human-assisted, automated. The agent replies where the team already is, and the live channels are Slack and Microsoft Teams, with email experimental and per project. The web app and the CLI start the same session. When the agent reaches your tools, 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP, and connector credentials are brokered server-side and never enter the machine.

## What a team hands back

The output of a session is a file, a fix or a report. Four jobs a team commonly hands to an agent on its own cloud computer:

- Support triage: sort the overnight queue, draft the repeatable replies, and flag the rest for a person. A run on placeholder accounts Northwind and Globex groups 38 tickets, drafts 12 replies, and escalates 5.
- Error triage: reproduce the day's worst error on its own machine, patch it, and open a change request. A run groups 9 error groups, fixes the top one, and passes 118 tests before a person reviews it.
- Ops report: pull last week's numbers from the connected tools and return a short digest a manager can read, with every figure linked to its source.
- Month-end close: match the ledger against the bank, chase the missing receipts, attach them, and close the month with the variance explained.

Those figures are illustrative sample data.

## When Kortix is the answer

A chat tool ends the turn at the reply, which is the right place to stop for a question. An agent platform is what a team needs when the answer has to become a change in a real system, with a machine that ran it and a person who approved it on record. Governance travels with that platform: one isolated sandbox per session, per-resource permissions for people and agents, roles, groups, and an audit trail, plus SAML 2.0 single sign-on and SCIM 2.0 for a security review.

Start from one repo and hand an agent its first job. [Try Kortix](https://kortix.com), or read the code at [Kortix on GitHub](https://github.com/kortix-ai/suna).
