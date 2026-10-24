# AI operating system claimants

This open-source record of the "AI operating system" field keeps what each claimant says about itself, in its own words, with the source URL. Eleven products now put those words on their own pages or repositories, and no two of them mean the same thing. A script re-checks every quote, so the record cannot quietly go stale.

```
python3 check.py
```

It fetches each vendor page, looks for the exact quote this repo stored, and exits non-zero when one has changed. Stdlib only: no keys, no accounts, no dependencies.

## What each one says

| | Cloudflare OS | Red Hat AI OS | VAST AI OS | Xyne | OpenFang | Paperclip |
|---|---|---|---|---|---|---|
| Calls itself | an operating system for AI productivity | a standard AI operating system (AI OS) | The VAST AI Operating System | an open-source operating system for organizations | The Agent Operating System | the app people use to manage AI agents for work |
| Says it is open source | yes | yes | no claim on its own page | yes | yes, though its metadata and README disagree on which licence | yes, MIT |
| Unit of work | a gadget, one private app instance per person | an inference workload | a dataset and the GPUs that serve it | a row in a shared context store | a Hand, a scheduled agent run started from one dashboard | a task in a company of agents, with an org chart and budgets |
| Documented production path | deploy into a Cloudflare account | a standardized layer on existing open-source infrastructure | a platform sold by the vendor | on infrastructure the organization controls | one binary on the operator's machine | a Node.js server and React UI you run; a cloud edition sits on a waitlist |
| Status | version 2, early access, August 2026 rewrite | a position in a vendor blog post | product page | All Things Open 2026 community post | v0.6.9, May 2026, still pre-1.0 | active MIT repository, October 2026 |

Every cell traces to the vendor's own page or repository README, listed in `claimants.yaml` and checked by `check.py`. Where a vendor's page does not state something, the cell says so rather than filling the gap from a summary.

## Four more, added October 2026

The first six are companies selling a platform. These four are the other shape the phrase attracts: small, self-hosted systems whose authors ship a repository and an install script. Three of them claim the words "agent operating system" or "agentic operating system" verbatim, which is why they are in this record.

| | taOS | Klawty | SanctumOS | CorvinOS |
|---|---|---|---|---|
| Calls itself | "the self-hosted AI agent operating system" | "The AI Agent Operating System" | "The Modular, Self-Hosted Agentic Operating System" | "The operating system for AI work" |
| Says it is open source | its page says source-available; its repository is AGPL-3.0 | yes: "Open-source AI agent operating system with enterprise security", MIT, printed beside the download | no open-source claim on its own page; its two module repositories report no recognised licence | yes, Apache-2.0 |
| Unit of work | a personal cloud on hardware you own: one memory graph (taOSmd), agents, channels and the bundled apps in its store | an always-on agent taking tasks from a channel: its own numbers read 1,000+ tasks, 20+ channels, 52 skills, a hardened fork of OpenClaw | a module with a brain-region name (Thalamus, Broca, Cochlea) wired to a tool server, SMCP | a turn routed to the cheapest model that can answer it, with fail-closed gates on the way out |
| Documented production path | install on your own board or machine from its installer scripts; cloud models are opt-in, and it announces a paid convenience layer for access from outside your network | `curl -fsSL https://klawty.ai/install.sh \| bash`, Docker ready, built on OpenClaw | deploy the modules on your own infrastructure from their repositories, following the docs | `curl -fsSL https://corvin-labs.com/install.sh \| sh` clones the repository and runs its installer, the console on 127.0.0.1:8765 |
| Status | v1.0.0-beta.56, 15 October 2026, still beta, AGPL-3.0 | site advertises v1.4.0; the public repository has no release or tag, last push 19 June 2026 | version 1.2 on its own structured data, latest post 13 October 2026 | tier1-complete, 18 September 2026, repository active |
| The gap to check | source-available is not the same claim as open source, and the release is a beta | the licence is permissive, but a version number on a website is not a release you can pin | "self-hosted" is stated, open source is not | the routing and the gates are documented; how much runs locally depends on the model providers you point it at |

The row to read twice is the open-source one. A page can say "self-hosted" and mean only that the installer is yours to run, and a repository can carry a permissive licence while the version a visitor downloads is the author's convenience build. That is why each entry records the licence as the repository reports it, not as the marketing page implies it.

## The newest claimant is a platform, not a product

Microsoft put the name on a device platform at Build 2026. Project Solara is "a chip-to-cloud platform, codenamed Project Solara, designed from the ground up for agent-first experiences" in Microsoft's own words, and the parts it names are a device operating system, not a company's agent layer:

- **What runs on the device:** MDEP, described by Microsoft as "an enterprise-grade operating system built on AOSP", plus an Agent Shell that "can dynamically load and tailor multiple cloud-based agents".
- **Who manages it:** Microsoft Intune for the fleet and Entra ID for sign-in, with Hello for Business, a physical microphone mute and approved chipsets listed as device attributes.
- **What it sits on:** Azure. Microsoft's own briefing to GeekWire names Azure as where the devices' agents run, and says Microsoft will not ship the devices itself: hardware partners build them, with AccuWeather, Best Buy, CVS Health, Levi's and Target named as expected pilot customers.
- **What it does not state:** no open-source claim appears on the platform page. Microsoft calls the project early ("I don't want to over-promise") and the two concept devices a starting point.

That makes Solara the cleanest example of the split this record keeps running into. A device platform decides what runs on a badge or a desk hub and who patches it. It leaves open the question this repo asks of every claimant: where do the definitions of the agents, their grants and the company's memory live, and can the company fork them. Microsoft's answer is cloud agents delivered through an Agent Shell and policy held in Intune and Entra; the comparison against the company-layer answer is at [Microsoft Project Solara and the open-source layer it leaves to you](https://opensourceaioperatingsystem.com/microsoft-project-solara).

## Why the record is worth keeping

The phrase is doing a different job for every claimant. Read the pages and the disagreement is not about features, it is about what the operating system is *for*:

- Cloudflare OS treats a person's private app instance as the unit, and its security model, Gatekeepers, exists to make it safe for someone non-technical to build one.
- Red Hat's post argues for an inference layer, a standard runtime for serving models across hardware, and says plainly it is not an operating system built from scratch.
- VAST's page is a data platform: storage, ingestion, vector search and runtime pulled into one layer.
- Xyne's post argues the unit is a row in a context store the organisation owns, with approval and ownership staying with a person.
- OpenFang treats the unit as a scheduled run: one Rust binary on one machine, with a SQLite memory file and a hash-chained log beside it. Its README calls it pre-1.0 and still says to pin a commit.
- Paperclip treats the unit as a task inside a company: an org chart of agents, budgets per agent, and an "Agentic OS" pillar covering runtime, SSO and RBAC. It orchestrates other vendors' agents rather than supplying the runtime itself.

None of those is the same product decision, so "which AI operating system" is not answerable until you say which job you have: an app, a workload, a dataset, a context store, a schedule, a company of agents, a personal cloud, a routed turn, or a session.

## The fifth entry this table does not have

[Kortix](https://kortix.com) is an open-source AI Operating System whose unit of work is a session: each session runs on its own cloud computer, works on a branch of a project the company owns, and reaches the main branch through a change request. It is not in the table above because the table records vendors competing for one phrase, and the point of the repo is to keep that record checkable, not to rank anyone. Read it and judge for yourself, or start with the [docs](https://kortix.com/docs).

## Layout

```
claimants.yaml   what each vendor says, with source URLs and the exact quote
check.py         re-fetch and confirm; exits 1 on drift
docs/            three short notes: what counts, the open-source question, the deployment question
```

## Contributing

If a vendor changed its page, open an issue with the URL and the new sentence, or send a pull request that updates `claimants.yaml` and the table together. Run `check.py` before you push: a quote that does not appear on the source page is the one thing this repository refuses.

## The pages these claims feed

The record here is the evidence behind one comparison: [four claimants of the name, and how to tell them apart](https://opensourceaioperatingsystem.com/open-source-ai-operating-system-compared) is the prose version, and [what an AI operating system is when a company deploys it](https://opensourceaioperatingsystem.com/ai-operating-system-for-companies) is where the deployment question ends up. The three senses of the name, and which products hold each, are set out in [what AI OS means](https://opensourceaioperatingsystem.com/what-is-aios). Cloudflare OS is the newest claimant in the set, and [the Cloudflare OS alternative page](https://opensourceaioperatingsystem.com/cloudflare-os-alternative) is the version of that comparison for a team already running it. OpenFang's single-binary shape and [the OpenFang alternative page](https://opensourceaioperatingsystem.com/openfang-alternative) cover the case where the runtime stays on one machine, and [the Agent OS explainer](https://opensourceaioperatingsystem.com/agent-os) sorts a runtime from a spec kit from a hosted feature. The device-side claimant has its own page: [Microsoft's Project Solara](https://opensourceaioperatingsystem.com/microsoft-project-solara) separates a device platform from the layer that holds a company's agents.

