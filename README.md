# Cody Kickertz

Systems engineer. I build sovereign infrastructure in Rust: cognitive agents, media automation, RF intelligence. Everything runs on commodity hardware with no cloud dependencies. Everything is open source.

All three projects share a naming philosophy ([gnomon](gnomon.md)), a unified [development methodology](WORKFLOW.md), and a conviction that the tools you depend on should be tools you own.

---

## Projects

### [Aletheia](https://github.com/forkwright/aletheia)

*ἀλήθεια: unconcealment, disclosure of what is*

Multi-agent cognitive runtime. Persistent memory, adaptive recall, and tool execution in a single Rust binary.

- 17 specialized crates (~194K lines of Rust): agent orchestration (Tokio actors), LLM routing, planning, domain knowledge packs, behavioral evaluation
- Six-factor memory recall: FSRS power-law decay, epistemic confidence tiers (verified > inferred > assumed), graph relationship proximity, vector similarity (HNSW), and behavioral pattern learning
- Zero external services: vendored CozoDB (Datalog + relational + vector), SQLite sessions, candle embeddings. Only your LLM API key leaves the machine
- Each agent is a Tokio actor with persistent character, workspace, and memory. Agents coordinate through a bi-temporal knowledge graph, not message queues
- Per-message XChaCha20Poly1305 encryption at rest. No telemetry. Every network call documented and auditable
- TUI (ratatui), desktop app (Tauri), HTTP API (Axum)

`Rust` `AGPL-3.0`

### [Harmonia](https://github.com/forkwright/harmonia)

*ἁρμονία: the joining together of disparate things*

Unified media platform replacing the *arr ecosystem. One system handles discovery, download, organization, metadata, serving, and playback for all media types.

- Single Rust backend (Mouseion: 10 crates, Tokio + Axum + SQLx) managing movies, TV, music, audiobooks, ebooks, podcasts, manga, comics, news
- Built-in Torznab/Newznab indexing, BitTorrent client, archive extraction, subtitle management, quality profiles, and household request workflow. No Sonarr, Radarr, Lidarr, Prowlarr, Jackett, qBittorrent, Overseerr, or their 15+ satellite tools
- Multi-platform player (Akouo) for Android (Kotlin/Compose), web (React 19), and desktop (Tauri). Bit-perfect audio core: symphonia decoding, rubato resampling, EBU R128 loudness, gapless playback
- QUIC streaming (quinn) for multi-room sync. Event-driven subsystem architecture (aggelia bus). Integrates Last.fm, Tidal, Plex

`Rust` `Kotlin` `TypeScript` `C#` `GPL-3.0`

### [Akroasis](https://github.com/forkwright/akroasis)

*ἀκρόασις: attentive reception, learning through disciplined listening*

RF intelligence, mesh networking, and communications sovereignty. 17 crates across 10 capability domains unified under a single typed signal model.

- Every collection domain (radio, mesh, SDR, proximity, network defense, OSINT, offensive security) produces typed GeoSignal objects into a shared model (koinon). Processing is domain-agnostic: semaino reads signs in the noise, ichneutes follows the tracks to focal points, praxis converts understanding into action
- Standalone Meshtastic stack (kerykeion): clean-room protobuf, delay-tolerant networking, PACE communications with automated failover. CHIRP-compatible radio programming (syntonia) for Baofeng and Yaesu hardware
- SDR pipeline (dektis): FutureSDR async block graphs, FM/AM/SSB demodulation, APRS/ADS-B/P25 decoding, jamming detection, direction finding, emitter fingerprinting via RTL-SDR and HackRF
- Suricata/Zeek orchestration (aspis) for network defense with active response. WiFi/BLE/Zigbee/NFC/RFID proximity monitoring (engys). Offline knowledge repository (pinax) with frequency databases, protocol specs, topo maps, emergency procedures
- Grid-down capable. No cloud. Encrypted by default. Tamper-evident logging with hash chains and chain-of-custody evidence packaging. NixOS reproducible deployment
- Lethe (λήθη: concealment) handles privacy, VPN orchestration, OPSEC scoring, and IMSI catcher detection. Same root as Aletheia, opposite direction: one unconceals truth, the other conceals the operator

`Rust` `AGPL-3.0`

---

## How It Gets Built

These projects are built using [closed-loop agentic development](WORKFLOW.md): structured prompts as units of work, parallel agent dispatch, automated QA gates, and corrective loops that fix their own failures. Rust's compiler is the QA layer. The human decides what gets built and why. The system builds it.

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
# Cody Kickertz

Systems engineer. I build sovereign infrastructure in Rust: cognitive agents, media automation, RF intelligence. Everything runs on commodity hardware with no cloud dependencies. Everything is open source.

All three projects share a naming philosophy ([gnomon](gnomon.md)), a unified [development methodology](WORKFLOW.md), and a conviction that the tools you depend on should be tools you own.
