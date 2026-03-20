# Cody Kickertz

Systems engineer. I build sovereign infrastructure in Rust: cognitive agents, media automation, RF intelligence, mobile OS. Everything runs on commodity hardware with no cloud dependencies.

Five projects share a naming philosophy (naming discipline), a unified development system, and a conviction that the tools you depend on should be tools you own.

---

## Projects

### [Aletheia](https://github.com/forkwright/aletheia)

*ἀλήθεια: unconcealment, disclosure of what is*

Multi-agent cognitive runtime. Persistent memory, adaptive recall, and tool execution in a single Rust binary.

- 20 specialized crates (~238K lines of Rust): agent orchestration (Tokio actors), LLM routing, planning, domain knowledge packs, behavioral evaluation
- Hybrid recall: FSRS power-law decay, epistemic confidence tiers, graph relationship proximity, vector similarity (HNSW), BM25 full-text search, MMR diversity filtering
- Zero external services: embedded Datalog+HNSW engine (71K LOC, rewritten from CozoDB), bundled SQLite sessions, candle embeddings. Only your LLM API key leaves the machine
- Each agent is a Tokio actor with persistent character, workspace, and memory. Agents coordinate through a knowledge graph with ecological succession and conflict detection
- Per-message XChaCha20Poly1305 encryption at rest. Landlock + seccomp sandbox. Pure Rust syscalls via rustix. No libc, no telemetry
- TUI (ratatui), desktop app (Dioxus), HTTP API (Axum), Signal messenger

`Rust` `AGPL-3.0`

### [Harmonia](https://github.com/forkwright/harmonia)

*ἁρμονία: the joining together of disparate things*

Unified media platform replacing the *arr ecosystem. One system handles discovery, download, organization, metadata, serving, and playback for all media types.

- Single Rust backend (Mouseion: 10 crates, Tokio + Axum + SQLx) managing movies, TV, music, audiobooks, ebooks, podcasts, manga, comics, news
- Built-in Torznab/Newznab indexing, BitTorrent client, archive extraction, subtitle management, quality profiles, and household request workflow. No Sonarr, Radarr, Lidarr, Prowlarr, Jackett, qBittorrent, Overseerr, or their satellite tools
- Multi-platform player (Akouo) for Android (Kotlin/Compose), web (React), and desktop. Bit-perfect audio core: symphonia decoding, rubato resampling, EBU R128 loudness, gapless playback
- QUIC streaming (quinn) for multi-room sync. Event-driven subsystem architecture (aggelia bus)

`Rust` `Kotlin` `TypeScript` `GPL-3.0`

### [Akroasis](https://github.com/forkwright/akroasis)

*ἀκρόασις: attentive reception, learning through disciplined listening*

RF intelligence, mesh networking, and communications sovereignty. 17 crates across 10 capability domains unified under a single typed signal model.

- Every collection domain (radio, mesh, SDR, proximity, network defense, OSINT) produces typed GeoSignal objects into a shared model (koinon). Processing is domain-agnostic: semaino reads signs in the noise, ichneutes follows the tracks, praxis converts understanding into action
- Standalone Meshtastic stack (kerykeion): clean-room protobuf, delay-tolerant networking, PACE communications with automated failover. CHIRP-compatible radio programming (syntonia) for Baofeng and Yaesu hardware
- SDR pipeline (dektis): FutureSDR async block graphs, FM/AM/SSB demodulation, APRS/ADS-B/P25 decoding, direction finding, emitter fingerprinting via RTL-SDR and HackRF
- Grid-down capable. No cloud. Encrypted by default. Tamper-evident logging with hash chains and chain-of-custody evidence packaging
- Lethe (λήθη: concealment) handles VPN orchestration, OPSEC scoring, and IMSI catcher detection. Same root as Aletheia, opposite direction: one unconceals truth, the other conceals the operator

`Rust` `AGPL-3.0`

### [Thumos](https://github.com/forkwright/thumos)

*θυμός: spirited part of the soul, seat of courage and indignation*

Sovereign mobile operating system. Full Rust from kernel to UI, built for the AGM M7 rugged keypad phone. No Linux kernel, no C we author.

- Custom monolithic kernel (pyknosis): ARM boot, MMU, GIC, timer, process scheduler, syscalls, IPC, ELF loader, RAMFS, device registry, power management, debug console
- 13 userspace crates: phone (AT modem, CCCI), eidolon (framebuffer UI), asphaleia (packet filter), sema (WiFi/IMSI detection), stegnos (disk encryption), krypta (Signal protocol), leipsanon (panic mode), pteron (BLE), kelyphos (STP framing), aither (WPA), topos (GPS), haphe (input)
- Hardware kill switches for radios, sensors, USB data. Non-software-overridable
- Motivated by a 10-minute surveillance audit that found seven threat vectors across three nation-states in the stock firmware

`Rust` `AGPL-3.0`

### Kanon

*κανών: the measuring rod, the rule by which all else is judged*

Development standards toolkit and agentic dispatch system. The canonical source for coding standards, prompt management, and workflow automation across all forkwright repositories. Private repository.

- 22 coding standards documents (7,500+ lines) covering Rust, Python, TypeScript, Shell, SQL, Nix, and 6 other languages
- Automated lint engine (basanos) enforcing standards against every file in every repo
- Agentic dispatch: structured prompts dispatched to parallel Claude sessions with graduated resume, QA gates, and corrective loops
- Steward role: autonomous CI manager that classifies failures, fixes broken PRs, and auto-merges green ones
- Training data capture from every dispatch, lint run, and QA review for local model fine-tuning

`Rust` `Python` `AGPL-3.0`

---

## How It Gets Built

These projects are built using closed-loop agentic development: structured prompts as units of work, parallel agent dispatch, automated QA gates, and corrective loops that fix their own failures. The compiler is the QA layer. The human decides what gets built and why. The system builds it.

---

## Professional

**Data Scientist & AI Systems Architect** at Summus Global. Clinical NLP pipelines, medical taxonomy systems, GenAI analysis infrastructure.

**Former:** USMC Captain, Finance Officer. Cybersecurity research with Clarkson Aerospace & AFRL.

**Education:** MBA, UT Austin McCombs (2026). BS Computer Information Systems, University of Houston.

---

## Other

**[Ardent Leatherworks](https://ardentleatherworks.com)** : Small-batch leather goods.

**The Coherence of Aporia** : A book on cognition, craft, AI topology, and the structure of contradictions that hold.

---

[LinkedIn](https://linkedin.com/in/cody-kickertz/)
