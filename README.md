Rust systems — an agent runtime, a media platform, RF and signals tooling, a bare-metal phone OS — and the libraries shared underneath them. Repo names are Greek; each entry below carries its translation.

## Systems

### [Aletheia](https://github.com/forkwright/aletheia) — agent runtime
*ἀλήθεια: unconcealment*

Agent runtime with persistent session memory, a local knowledge store, Datalog reasoning, a tool registry, and multi-provider model dispatch across remote and local models. Desktop UI built on theatron.

`Rust` `AGPL-3.0`

### [Harmonia](https://github.com/forkwright/harmonia) — media platform
*ἁρμονία: the joining together of disparate things*

Unified media system — library backend, format conversion, request and approval workflows, and Android playback. One coherent backend replacing a pile of loosely-coupled tools.

`Rust` `AGPL-3.0`

### [Akroasis](https://github.com/forkwright/akroasis) — RF and signals
*ἀκρόασις: attentive reception*

RF observation and control, Meshtastic mesh networking with multi-gateway failover, geo-signal aggregation with anomaly alerting, and an encrypted credential vault — a single typed model of signal collection and interpretation.

`Rust` `AGPL-3.0`

### [Thumos](https://github.com/forkwright/thumos) — mobile OS
*θυμός: the spirited part of the soul*

From-scratch bare-metal Rust OS for the AGM M7 (MediaTek MT6739): custom kernel — MMU, scheduler, IPC, VFS — with userspace for modem AT handling, Signal-protocol messaging, packet filtering, and encrypted storage. No Linux in the final system. Hardware bring-up pending.

`Rust` `PolyForm Shield 1.0.0`

### [Logismos](https://github.com/forkwright/logismos) — GPU inference
*λογισμός: reasoning, calculation*

From-scratch GPU inference stack for AMD hardware (HIP + hipBLASLt, gfx1100): hand-written WMMA kernels living beside the Rust that launches them, with CPU reference implementations gating correctness. Transformer embedding models run end-to-end on CPU; the GPU cutover is blocked on hardware availability.

`Rust` `PolyForm Shield 1.0.0`

### [Hamma](https://github.com/forkwright/hamma) — mesh networking
*ἅμμα: a knot, a tie, a fastening*

Clean-room, Tailscale-compatible mesh networking client: Noise handshake, control protocol, peer registration, map streaming. The WireGuard data plane is not wired yet. Pre-alpha.

`Rust` `MIT OR Apache-2.0`

## Libraries

### [Theatron](https://github.com/forkwright/theatron) — desktop UI infrastructure
*θέατρον: the seeing-place*

Dioxus/Blitz UI primitives, design-token discipline, markdown rendering, an HTTP/SSE client, and OS integration. Consumed by aletheia as a pinned git dependency.

`Rust` `MIT OR Apache-2.0`

### [Sphragis](https://github.com/forkwright/sphragis) — post-quantum sealing
*σφραγίς: a seal*

X-Wing hybrid KEM (X25519 + ML-KEM-768) with a ChaCha20-Poly1305 envelope. Unaudited preview behind an explicit feature flag.

`Rust` `AGPL-3.0`

### [Koinon](https://github.com/forkwright/koinon) — common scaffolding
*κοινόν: that which is shared*

Tracing init, typed errors, config loading, and a CLI prelude.

`Rust` `Apache-2.0`

### [Epitelesis](https://github.com/forkwright/epitelesis) — subprocess substrate
*ἐπιτέλεσις: executing-to-completion*

Typed command-execution wrapper over the std and tokio process APIs — timeouts as contract, concurrent pipe draining, typed errors carrying captured output. Every subprocess in the kanon toolkit goes through it.

`Rust` `Apache-2.0 OR MIT`

### [Heurema](https://github.com/forkwright/heurema) — search primitives
*εὕρημα: a thing found*

Contracts for vector search, full-text search, persistence, and rank fusion. Reciprocal-rank fusion is implemented; HNSW and BM25 land by extraction from their in-app implementations.

`Rust` `AGPL-3.0`

### [Zetesis](https://github.com/forkwright/zetesis) — research substrate
*ζήτησις: systematic inquiry*

Budget, cost, citation, and query contracts for agent research pipelines, with a fixture-driven deep-research loop. Phase-1 scaffold; provider integrations pending.

`Rust` `AGPL-3.0`

## Web

### [Typikon](https://github.com/forkwright/typikon) — site substrate
*τυπικόν: the book of order*

Zola theme, JSON-Schema frontmatter validation, scaffolding scripts, and a CI gate bundle — CSP enforcement, link checking, accessibility, smoke tests — consumed by fleet sites as a git submodule.

`Zola` `AGPL-3.0`

### [Epistole](https://github.com/forkwright/epistole) — newsletter service
*ἐπιστολή: a letter*

Subscriber lifecycle — subscribe, confirm, unsubscribe — and archive flows over an embedded store. SMTP delivery is the next phase.

`Rust` `AGPL-3.0`

## In design

### [Pinax](https://github.com/forkwright/pinax) — relational storage engine
*πίναξ: the tablet, the register — the Pinakes of Callimachus were the first structured index of knowledge*

Relational storage engine designed from scratch in Rust: multi-writer MVCC, per-page encryption, causal changelog as a storage primitive, strict typing, zero C dependency. Replaces SQLite across the fleet. Design phase; no code yet.

`PolyForm Shield 1.0.0`

### [Mneme](https://github.com/forkwright/mneme) — deductive storage engine
*μνήμη: memory as faculty*

Datalog engine for facts, rules, and inference — content-addressed facts with supersede-based retraction, unified provenance, incrementally maintained views. The engine exists inside aletheia today and promotes here once it clears its overhaul phases. Design phase.

`PolyForm Shield 1.0.0`

### [Dioptron](https://github.com/forkwright/dioptron) — web runtime
*δίοπτρον: the instrument through which one sees*

Specification and requirements for a web runtime where operator and agents share one capability surface — browsing, ingesting, querying, and acting — instead of splitting human and machine workflows into separate stacks. Design documents only; implementation not started.

`AGPL-3.0`

## Professional

**Data Scientist & AI Systems Architect** at Summus Global. Clinical NLP, medical taxonomy, and GenAI analysis infrastructure.

**Former:** USMC Captain, Finance Officer. Cybersecurity research with Clarkson Aerospace & AFRL.

**Education:** MBA, UT Austin McCombs (2026). BS Computer Information Systems, University of Houston.

**Research:** Complex systems and the emergence of novel reasoning through topology.

## Other

**[Ardent Leatherworks](https://ardentleatherworks.com)** — small-batch leather goods.

[LinkedIn](https://linkedin.com/in/cody-kickertz/)
