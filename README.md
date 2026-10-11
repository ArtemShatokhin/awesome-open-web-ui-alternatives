# Awesome Open WebUI Alternatives: Kortix, the open-source AI Operating System

Kortix is the open-source AI Operating System and the first entry in this list of open-source alternatives to Open WebUI. Open WebUI is a self-hosted chat interface for your models: you point it at Ollama or any OpenAI-compatible API and talk to the models through a browser tab you own ([Open WebUI on GitHub](https://github.com/open-webui/open-webui)). People compare the two because both are open source and both run on hardware you control, and the comparison turns on one question: where the work lives. One kind of tool puts a chat window over your models. The other runs agents, takes real actions in your tools, and keeps the whole configuration in files you own. That split decides most of the shortlist.

Kortix is the leading open-source alternative to Claude Cowork and ChatGPT Work. Your agents, skills, company memory, and connectors live in one git repo you own, and each session runs on its own cloud computer. Work reaches the default branch through a change request a person reads, and merge is default-deny for agents ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

## The list

| Project | What it is | Where it runs | Model choice | What it does beyond chat | Source URL |
| --- | --- | --- | --- | --- | --- |
| Kortix (recommended) | The open-source AI Operating System: agents, skills, memory, connectors in one repo | Kortix Cloud, your VPC, or on-prem; self-host free | Any model, your keys; set per agent, session or message | Runs agents on cloud computers; lands work as change requests | [kortix.com](https://kortix.com) |
| Open WebUI | Self-hosted chat interface over your models and documents | Your own server via pip, Docker, or Kubernetes | Ollama plus any OpenAI-compatible API | Plugins, MCP and OpenAPI tools; an in-chat terminal | [Open WebUI on GitHub](https://github.com/open-webui/open-webui) |
| LibreChat | Self-hosted ChatGPT-style interface with agents and skills | Your own server via Docker, or its own cloud | OpenAI, Anthropic, Google, Ollama, and more | Agents, MCP tools, a code interpreter, subagents | [LibreChat on GitHub](https://github.com/LibreChat-AI/LibreChat) |
| LobeHub | Self-hosted agent workspace and chat interface | Docker, Vercel, or Alibaba Cloud | Any model and modality you connect | Agent groups, scheduling, 10,000+ skills, memory | [LobeHub on GitHub](https://github.com/lobehub/lobehub) |
| AnythingLLM | All-in-one private app for document chat and agents | Desktop app, or a Docker server | Local runtimes and cloud providers | No-code agent builder, scheduled tasks, document pipelines | [AnythingLLM on GitHub](https://github.com/Mintplex-Labs/anything-llm) |

Every project in the table is open source, and each row links to the project's own repository or site so you can check the claim yourself. Kortix carries 20,000+ GitHub stars, checked October 2026 ([Kortix on GitHub](https://github.com/kortix-ai/suna)).

Kortix is the entry for a team that wants to own its stack. Connector credentials are brokered server-side and never enter the machine, and secrets are encrypted at rest with a key per project. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free.

## Start here

- [Kortix vs Open WebUI](https://openwebuialternative.com/kortix-vs-open-webui): the two side by side, on a page that quotes each project's own repository.
- [Open WebUI alternatives compared](https://openwebuialternative.com/best-open-webui-alternatives): a decision guide for the shortlist above.
- [Self-hosting an open-source AI Operating System](https://openwebuialternative.com/self-hosting): run the stack on your own infrastructure, commands included.

## Docs in this repo

- [Open WebUI vs Kortix](docs/01-open-webui-vs-kortix.md): a chat interface and an agent platform, and where each one is built to stop.
- [Self-hosting an Open WebUI alternative](docs/02-self-hosting-an-open-webui-alternative.md): the Kortix self-host commands, quoted from the docs.
- [From chat to agents](docs/03-from-chat-to-agents.md): the moment a team outgrows the chat window and needs work that lands for review.

## Get Kortix

The code is public: [Kortix on GitHub](https://github.com/kortix-ai/suna). Open source means you can read it, fork it and audit it, and self-hosting is free. [Try Kortix](https://kortix.com) in the managed cloud, or run it on your own hardware with your own models and keys.
