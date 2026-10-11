# Self-hosting Kortix: run the open-source AI Operating System on your own box

Kortix is the open-source AI Operating System, and it self-hosts as one Docker Compose stack: the frontend, the API, the LLM gateway, and the Supabase distribution ([Self-hosting docs](https://kortix.com/docs/host)). Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. Agent sessions run on a separate sandbox provider, so the control plane you host stays small, and the stack has no Redis and no separate worker to operate. The [self-hosting guide on the comparison site](https://openwebuialternative.com/self-hosting) covers the same ground for a general audience.

## What you own when you self-host

Self-hosting Kortix means the repo, the connectors, the models and the memory sit on your infrastructure. Your agents, skills, company memory, and connectors live in one git repo you own. An agent is `agents/<name>.md` (behavior) plus an `agents.<name>` block in `kortix.yaml` (governance), and `kortix.yaml` declares the machine image, connectors and triggers, and secret names and grants. Because the setup is a repo, you can grep the whole company, diff any change, and roll any part of it back. Memory is files that accumulate next to the agents that use them, so every fact the company learns is versioned and diffable like the rest of the repo.

Connector credentials are brokered server-side and never enter the machine. Secrets are encrypted at rest with a key per project, and their names and grants live in the manifest while the values never appear in the repo. One isolated sandbox per session, and each session has its own isolated machine and branch, so only what a session commits survives.

## Install it

The manual path installs the CLI, then initializes and starts the stack ([Self-hosting docs](https://kortix.com/docs/host)):

```bash
# 1 - install the CLI
curl -fsSL https://kortix.com/install | bash

# 2 - create an A/AAAA record for your domain and for api.<domain>,
#     open ports 80 and 443 (the bundled Caddy proxy issues TLS), then initialize
kortix self-host init --domain kortix.example.com

# 3 - start the stack
kortix self-host start
```

While the stack comes up, `kortix self-host status`, `kortix self-host logs` and `kortix self-host doctor` show what is happening. To try Kortix with no domain, use a Cloudflare tunnel instead of a domain. The tunnel URL changes on every restart, so use this mode for evaluation, not production ([Self-hosting docs](https://kortix.com/docs/host)):

```bash
kortix self-host init --tunnel cloudflare
kortix self-host start
```

After the stack starts, set your sandbox provider key. `kortix self-host configure` is an interactive prompt for the sandbox provider key, and optionally a managed-git token. The first run asks six things and no model key, GitHub connects in the dashboard (Settings, then Git), and models are BYOK in the app. A self-hosted instance uses your own key by default.

## Keep it running

Every instance updates itself automatically, or you can pin an exact version. Back up before a destructive command: an instance stores its data as two directories under `~/.config/kortix/self-host/<instance>/`, `volumes/db/data` for the Postgres database and `volumes/storage` for file storage, and the instance `.env` file holds every secret and signing key it uses ([Self-hosting docs](https://kortix.com/docs/host)).

```bash
# pin an exact version instead of auto-updating
kortix self-host update --tag 0.9.84

# on a 16 GiB host, raise the per-API-container memory limit
kortix self-host env set KORTIX_API_MEMORY_LIMIT=1024m
docker stats --no-stream
```

Each API container has a 640 MiB memory limit by default, which is the right default on an 8 GiB host ([Self-hosting docs](https://kortix.com/docs/host)).

## The model layer

Kortix is model-agnostic, so a self-hosted instance is not tied to one lab. Any model provider with your own keys, or the ChatGPT plan you already pay for, or sign in with your OpenCode Console account for OpenCode Zen and Go. Models are BYOK in the app, and you can set the model per agent, per session or per message.

Start self-hosted, or [Try Kortix](https://kortix.com) in the cloud first. The code is public at [Kortix on GitHub](https://github.com/kortix-ai/suna), open source, so you can read it, fork it and audit it.
