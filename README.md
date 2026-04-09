# Cody Kickertz

Systems engineer building self-sovereign infrastructure in Rust. Systems that think, sense, and communicate without depending on anything not required to be a dependency.

The public repositories here are the visible edge of a larger ecosystem built around local-first, dependency-conscious design and a strong preference for owned infrastructure over rented abstraction.

---

## Projects

### [Aletheia](https://github.com/forkwright/aletheia) — cognitive runtime

*ἀλήθεια: unconcealment*

Multi-agent AI system with persistent memory. Agents run as Tokio actors with character, workspace, and a knowledge graph that grows with every conversation. Embedded Datalog+HNSW engine, bundled SQLite, local embeddings via candle. One binary, no external databases, no cloud dependencies beyond an LLM API key. Encrypted at rest, sandboxed at the kernel level.

`Rust` `Kotlin` `AGPL-3.0`

### [Harmonia](https://github.com/forkwright/harmonia) — media platform

*ἁρμονία: the joining together of disparate things*

Replaces a ~ dozen-tool media management stack (Sonarr, Radarr, Prowlarr, qBittorrent, Overseerr, etc.) with one Rust backend handling discovery, download, organization, and serving for all media types. Multi-platform player with bit-perfect audio and QUIC multi-room sync.

`Rust` `Kotlin` `GPL-3.0`

### [Akroasis](https://github.com/forkwright/akroasis) — signals intelligence

*ἀκρόασις: attentive reception*

RF intelligence, mesh networking, and communications sovereignty. 17 crates across 10 domains (radio, SDR, mesh, proximity, network defense, OSINT) unified under a single typed signal model. Standalone Meshtastic stack, SDR pipeline for RTL-SDR and HackRF, CHIRP-compatible radio programming. Grid-down capable. Lethe (λήθη: concealment) handles VPN, OPSEC scoring, and IMSI catcher detection — same root as Aletheia, opposite direction.

`Rust` `AGPL-3.0`

### [Thumos](https://github.com/forkwright/thumos) — sovereign mobile OS

*θυμός: spirited part of the soul*

Full Rust from kernel to UI, built for the AGM M7 rugged keypad phone. Custom monolithic kernel, 13 userspace crates covering phone, UI, encryption, packet filtering, Signal protocol, and GPS. Hardware kill switches for radios, sensors, and USB data. Motivated by a surveillance audit that found seven threat vectors across three nation-states in the stock firmware.

`Rust` `AGPL-3.0`

### [Plegma](https://github.com/forkwright/plegma) — mesh networking

*πλέγμα: a woven thing, a plaited mesh*

Clean-room Rust implementation of a Tailscale-compatible mesh networking stack. The `dictyon` client speaks wire-compatible Noise control protocol to join existing tailnets and establishes WireGuard peer sessions via boringtun. A future `histos` coordination server replaces tailscale.com/Headscale for operators who want full sovereignty, with hardware-key-signed admin operations via FIDO2. Built because no production-grade Rust Tailscale client or server exists today. First consumer is Thumos; the whole forkwright ecosystem is the next step. Pre-alpha.

`Rust` `AGPL-3.0`

### Kanon — standards and automation

*κανών: the measuring rod*

Development standards toolkit and agentic dispatch system. Private repository.

The canonical source for coding standards, prompt management, and workflow automation across all forkwright projects. 25+ standards documents covering code, writing, architecture, security, testing, operations, and QA. Automated lint engine enforces every rule. Agentic dispatch sends structured prompts to parallel Claude sessions with QA gates and corrective loops. An autonomous steward manages CI, fixes failures, and merges clean PRs. Every dispatch, lint run, and review generates training data for local model fine-tuning.

`Rust` `Python` `AGPL-3.0`

---

## How it gets built

Closed-loop agentic development. Structured prompts as units of work, dispatched to parallel agent sessions. Automated QA gates validate output against kanon standards. Corrective loops fix their own failures. The compiler and lint engine are the quality floor. A dedicated agent reviews every commit before merge. Strategic direction is built in coordination with an infrastructure agent, then the system executes it.

---

## Professional

**Data Scientist & AI Systems Architect** at Summus Global. Clinical NLP, medical taxonomy, GenAI analysis infrastructure.

**Former:** USMC Captain, Finance Officer. Cybersecurity research with Clarkson Aerospace & AFRL.

**Education:** MBA, UT Austin McCombs (2026). BS Computer Information Systems, University of Houston.

**Research:** Complex systems and the emergence of novel reasoning through topology.

---

## Other

**[Ardent Leatherworks](https://ardentleatherworks.com)** — small-batch leather goods

**The Coherence of Aporia** — in progress. A book on cognition, craft, and the structure of contradictions that hold.

---

[LinkedIn](https://linkedin.com/in/cody-kickertz/)
