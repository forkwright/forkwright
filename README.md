Systems engineer building in Rust: cognition, media, communications, and the tooling that keeps them coherent. Local-first, dependency-conscious, owned infrastructure over rented abstraction.

The public repositories here are the visible edge of a larger fleet. English names mark user-facing applications; Greek names (dictyon, kerykeion, apotheke, themelion, …) mark shared infrastructure and cross-cutting concerns inside each app.

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

### [Hamma](https://github.com/forkwright/hamma) — mesh networking
*ἅμμα: a knot, a tie, a fastening*

Clean-room, Tailscale-compatible mesh networking client: Noise handshake, control protocol, peer registration, map streaming. The WireGuard data plane is not wired yet. Pre-alpha.

`Rust` `MIT OR Apache-2.0`

## Libraries

Extracted from the systems above on consumer pull, not speculation.

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

### [Dioptron](https://github.com/forkwright/dioptron) — web runtime
*δίοπτρον: the instrument through which one sees*

Specification and requirements for a web runtime where operator and agents share one capability surface — browsing, ingesting, querying, and acting — instead of splitting human and machine workflows into separate stacks. Design documents only; implementation not started.

`AGPL-3.0`

## How it gets built

Issue-driven, agent-executed, gate-anchored: structured prompts, isolated worktrees, parallel agent execution, a custom lint engine well past clippy (rule-precision tiers, suppression-as-violation, citation discipline), CI-exact local gates, and adversarial review before merge. Shared infrastructure follows a demand-pull rule: crates are extracted into standalone repos when consumers materialize, never speculatively.

The private side of the fleet carries the rest — the standards and dispatch control plane behind those gates, a GPU inference stack for local models, and a long-running research project on cognition, contradiction, and coherent systems that the naming and architecture grow out of.

## Professional

**Data Scientist & AI Systems Architect** at Summus Global. Clinical NLP, medical taxonomy, and GenAI analysis infrastructure.

**Former:** USMC Captain, Finance Officer. Cybersecurity research with Clarkson Aerospace & AFRL.

**Education:** MBA, UT Austin McCombs (2026). BS Computer Information Systems, University of Houston.

**Research:** Complex systems and the emergence of novel reasoning through topology.

## Other

**[Ardent Leatherworks](https://ardentleatherworks.com)** — small-batch leather goods.

[LinkedIn](https://linkedin.com/in/cody-kickertz/)
