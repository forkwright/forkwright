# Cody Kickertz

Systems engineer building sovereign software systems in Rust: cognition, media, communications, research infrastructure, and the tooling that keeps them coherent.

The public repositories here are the visible edge of a larger ecosystem built around local-first, dependency-conscious design and owned infrastructure over rented abstraction. English names mark user-facing applications; Greek names (basanos, archeion, mnemosyne, parodos, …) mark shared infrastructure and cross-cutting concerns inside each app.

GitHub is a mirror; primary authoring is forge-native.

## Public projects

### [Aletheia](https://github.com/forkwright/aletheia) — cognitive runtime
*ἀλήθεια: unconcealment*

Multi-agent AI runtime with persistent memory, local knowledge storage, and a multi-provider dispatch fleet that routes work to remote (Claude, Kimi K2) and on-premise (local Qwen3.5/Qwen3-Coder via logismos) models. The desktop UI layer is migrating to theatron.

`Rust` `AGPL-3.0`

### [Dioptron](https://github.com/forkwright/dioptron) — sovereign web runtime
*δίοπτρον: the instrument through which one sees*

Web substrate for operator and agent co-tenancy. One capability surface for browsing, ingesting, querying, and acting on the web without splitting human and machine workflows into separate stacks.

`Rust` `AGPL-3.0`

### [Harmonia](https://github.com/forkwright/harmonia) — media platform
*ἁρμονία: the joining together of disparate things*

Unified media system for discovery, download, organization, playback, and serving — replacing a pile of loosely-coupled tools with one coherent backend and operator experience.

`Rust` `AGPL-3.0`

### [Akroasis](https://github.com/forkwright/akroasis) — signals intelligence
*ἀκρόασις: attentive reception*

Communications and signals sovereignty: RF observation, mesh networking, proximity tooling, and network intelligence under a single typed model of signal collection and interpretation.

`Rust` `AGPL-3.0`

### [Thumos](https://github.com/forkwright/thumos) — sovereign mobile OS
*θυμός: spirited part of the soul*

Mobile operating system and device stack for rugged, operator-controlled hardware. From-scratch kernel targeting MT6739 silicon — collapses a hostile smartphone dependency chain into something inspectable and owned.

`Rust` `PolyForm Shield 1.0.0`

### [Hamma](https://github.com/forkwright/hamma) — mesh networking
*ἅμμα: a knot, a tie, a fastening*

Clean-room mesh networking stack aimed at Tailscale-class connectivity without surrendering the coordination layer to a third party. Pre-alpha.

`Rust` `AGPL-3.0`

### [Zetesis](https://github.com/forkwright/zetesis) — research substrate
*ζήτησις: systematic inquiry*

Research and search substrate for agent systems: free-first provider routing, self-hosted orchestration, budget enforcement, caching, and cited result normalization.

`Rust` `AGPL-3.0`

## Internal infrastructure and research

**Kanon** *(κανών: the measuring rod)* — Self-hosted code forge (PRs, CI, issues) and control plane for the portfolio. Hosts workflow automation, multi-provider dispatch routing, and **basanos**: a custom lint engine that goes beyond clippy with rule-precision tiers, suppression-as-violation, citation discipline, and AI-trope detection. The GitHub-side repos are mirrors of forge state.

**Logismos** *(λογισμός: reasoning, calculation)* — Rust + HIP inference runtime targeting AMD W7900. Serves local Qwen models as the on-premise arm of the dispatch fleet.

**The Coherence of Aporia** — Long-running research project on cognition, contradiction, craft, and the structure of coherent systems. The architectural metaphors and naming convention emerge from it.

## How it gets built

Forge-native, closed-loop, issue-driven development. Structured prompts, isolated worktrees, parallel agent execution, and automated QA gates anchored on the basanos lint engine and human architectural review. Shared infrastructure follows a demand-pull rule: a `SHARED-INFRA.md` registry tracks crates with named cross-repo consumers; speculative shared crates are forbidden. Currently zero crates have earned promotion into the registry — the discipline is real.

## Professional

**Data Scientist & AI Systems Architect** at Summus Global. Clinical NLP, medical taxonomy, and GenAI analysis infrastructure.

**Former:** USMC Captain, Finance Officer. Cybersecurity research with Clarkson Aerospace & AFRL.

**Education:** MBA, UT Austin McCombs (2026). BS Computer Information Systems, University of Houston.

**Research:** Complex systems and the emergence of novel reasoning through topology.

## Other

**[Ardent Leatherworks](https://ardentleatherworks.com)** — small-batch leather goods.

[LinkedIn](https://linkedin.com/in/cody-kickertz/)
