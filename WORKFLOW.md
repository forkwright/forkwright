# Closed-Loop Agentic Development

The human is the architect. Everything else is the system.

---

## The Problem

Existing AI coding tools solve the single-session problem: one agent, one task, one PR. Software is not one task. It is a dependency graph of hundreds of tasks with ordering constraints, quality gates, cross-cutting concerns, and institutional knowledge that must survive across sessions.

The gap between "an agent can write a feature" and "agents can build a system" is not model capability. It is orchestration: who plans the work, who schedules it, who verifies it, who recovers from failure, and who ensures that knowledge from one session is available to the next.

This system closes every loop. A planner decomposes goals into structured prompts with machine-verifiable acceptance criteria. A dispatcher executes them in parallel across isolated worktrees. A QA gate evaluates each result against its criteria and controls what happens next: advance, correct, or block. A CI manager validates, auto-merges, and dispatches fix agents. An observation triage system converts ephemeral worker findings into tracked issues. The planner receives QA feedback and adjusts the plan.

The human approves plans, resolves ambiguity, and reviews held PRs. Everything between planning approval and merged code is autonomous.

---

## Roles

| Role | Responsibility | Intelligence |
|------|---------------|-------------|
| **Architect** | Final authority. Approves plans, resolves ambiguity, sets direction, reviews held PRs | Human |
| **Planner** | Decomposes goals into research and implementation prompts. Writes execution plans. Maintains standards. Receives QA feedback and adjusts plans | AI (high-capability model) |
| **Dispatcher** | Long-running orchestration service. Watches prompt queue, launches parallel sessions, monitors progress, runs QA, gates waves, generates corrective prompts | Automated (SDK + AI for QA/correction) |
| **Worker** | Executes a single prompt in an isolated worktree. Writes code, runs tests, opens a PR, captures observations | AI (headless session) |
| **CI Manager** | Validates PRs continuously. Auto-merges on green (policy-gated). Dispatches fix agents on failure. Triages observations post-merge | Automated (daemon + AI for fixes/triage) |

---

## Pipeline

```
Plan ──> Prompts ──> Dispatch ──> Execute ──> QA Gate ──> Merge
  ^                     ^                       │            │
  │                     │     PARTIAL/FAIL      │            │
  │                     └─── corrective ◄───────┘            │
  │                          prompts                         │
  │                                                          │
  │   verdicts + observations                                │
  └──────────────────────────────── Triage ──> Issues ───────┘
                                     │
                                     └──> next batch (dependencies unblocked)
```

---

## Core Concepts

**Prompt.** The atomic unit of work. A structured document containing a directive, task specification, acceptance criteria, blast radius, and validation gate. Machine-parseable, QA-verifiable, self-contained. A well-written prompt produces correct work regardless of which agent executes it. A poorly-written prompt produces plausible waste regardless of agent capability.

**Execution Plan.** A dependency DAG of prompts, partitioned into ordered batches. Prompts within a batch run in parallel. Batches run sequentially. Each prompt declares what it depends on and what it blocks. The plan is the schedule, the dependency tracker, and the progress dashboard in one artifact.

**Blast Radius.** The set of files and modules a prompt is authorized to modify. Not advisory — QA flags changes outside this boundary. Fix agents are constrained to it. Parallel prompts in the same batch declare non-overlapping blast radii, preventing merge conflicts by construction.

**Observation.** Something a worker noticed outside its task scope: a bug in adjacent code, missing tests, stale docs, a better API shape. Captured in the PR body. Automatically triaged into tracked issues post-merge. The mechanism that prevents ephemeral sessions from losing institutional knowledge.

**Verdict.** QA's assessment of a completed prompt. PASS, PARTIAL, or FAIL. Verdicts are not reports to be read — they are control signals that drive the dispatch loop: advance, correct, or block.

---

## Planning

The planner produces three artifact types.

### Research Prompts

Output is a document, not code. Findings with confidence levels, source citations, and actionable recommendations. Research establishes the facts that implementation prompts depend on. Architecture decisions are made here, not during implementation.

Research prompts execute in parallel waves. Later waves reference earlier results. The planner writes later waves after reviewing earlier outputs, not before.

### Execution Plans

A dependency DAG partitioned into ordered batches:

```
Batch 1: [001]                        # foundation, blocks everything
Batch 2: [002, 003]                   # parallel, both depend on B1
Batch 3: [004, 005, 006, 007]         # 4 parallel, all depend on B2
Batch 4: [008, 011]                   # depend on specific B3 outputs
Batch 5: [009, 010]                   # depend on 008
Batch 6: [012 -> 013 -> 014]          # sequential tail
```

Each prompt entry includes: dependencies, what it blocks, blast radius, model tier, and status. The plan is a living document — the dispatcher feeds QA verdicts and observation summaries back to the planner after each batch. The planner updates status, re-scopes later batches based on what was learned, and adjusts prompt specificity if the corrective rate is rising.

### Implementation Prompts

Output is a PR. The prompt is specific enough that two different agents executing the same prompt would produce structurally equivalent results. File listings, type definitions, function signatures, step-by-step validation commands. Ambiguity in a prompt produces ambiguity in the output. The planner's job is to eliminate ambiguity before dispatch.

---

## Prompt Structure

Every implementation prompt follows a fixed structure. Missing sections are errors, not review findings.

```markdown
# Task: <one-line description>

## Directive
Imperative execution framing. Forces implementation mode.

## Setup
Worktree creation and isolation.

## Standards
Project conventions (auto-populated).

## Context
What exists, what's decided. Minimal — only what the agent needs to start.

## Task
Exactly what to build. Imperative voice. Numbered steps if order matters.
Explicit exclusions for scope control.

## Acceptance Criteria
- [ ] Concrete, verifiable outcomes
- [ ] Each one is pass/fail testable
- [ ] QA evaluates the PR diff against these directly

## Blast Radius
Files and modules in scope. Changes outside this set are flagged by QA.

## Validation Gate
Project-specific checks: formatter, linter, tests.

## Observations
Capture anything noticed outside scope in the PR body.
Note file and line. Do not fix. Do not investigate deeply. Move on.
```

### Why Each Section Exists

| Section | Purpose | What breaks without it |
|---------|---------|----------------------|
| Directive | Forces execution mode | Agent analyzes the prompt instead of implementing it |
| Setup | Worktree isolation | Agent works on main, corrupts shared state |
| Standards | Project conventions | Agent writes valid code that violates project norms |
| Context | Orients without overloading | Agent makes wrong assumptions or drowns in irrelevant detail |
| Task | Defines the work | Ambiguous output, scope creep |
| Acceptance Criteria | Machine-verifiable outcomes | QA has nothing to evaluate against |
| Blast Radius | Scope boundary | Agent modifies unrelated files, creates merge conflicts |
| Validation Gate | Pre-PR checks | Broken PRs waste CI and review cycles |
| Observations | Knowledge capture | Findings from ephemeral sessions are permanently lost |

---

## Dispatch

The dispatcher watches the prompt queue, resolves dependencies against the execution plan, and forms groups for parallel execution.

### Orchestration Loop

```
for each group:
    sync repo to main
    launch all prompts in group as parallel headless sessions
    monitor progress (async, stuck detection)
    collect PRs

    QA gate (per-criterion evaluation):
        PASS    → mark complete, eligible for auto-merge
        PARTIAL → mark complete, generate corrective prompts, queue
        FAIL    → block dependent prompts, continue independents

    feed verdicts back to planner
    advance to next group
```

### Graduated Resume

When a session exhausts its turn budget, the dispatcher resumes with progressively narrower scope:

| Attempt | Turns | Instruction |
|---------|-------|-------------|
| Initial | 80 | Full prompt |
| Resume 1 | 40 | "Finish what you started. Do NOT start over." |
| Resume 2 | 20 | "Complete ONLY remaining acceptance criteria." |
| Exhausted | — | Mark stuck. Generate diagnostic scoped to what remains. |

The narrowing is deliberate. Resume 1 assumes the agent is close. Resume 2 forces re-orientation. After exhaustion, a diagnostic becomes input for a fresh prompt targeting exactly what's unfinished — the system builds forward, never backward.

---

## Verification

Three independent layers close the loop.

### Layer 1: QA Gate

Runs after each dispatch group. Per PR:

1. Fetch diff and file contents for modified files
2. Evaluate each acceptance criterion against the actual changes
3. Check blast radius compliance
4. Produce verdict: PASS, PARTIAL, or FAIL with per-criterion detail

Verdicts are control signals. PASS advances. PARTIAL generates a corrective prompt scoped to unmet criteria. FAIL blocks dependents and produces a diagnostic.

### Layer 2: CI Manager

Continuous validation of open PRs:

- **Trial merge** — detect conflicts before review
- **Validation gate** — format, lint, test suite
- **Auto-merge** — tiered policy (routine changes merge automatically, multi-module or public API changes are held for architect review)
- **Fix agents** — on CI failure, dispatch a constrained fix agent (file-scoped, diff-capped) before escalating to human
- **Observation triage** — post-merge, parse PR body for observations, create tracked issues

### Layer 3: Planner Feedback

The planner receives:
- QA verdicts per prompt (which criteria passed, which failed, why)
- Observation summaries (cross-cutting findings from workers)
- Health metrics (corrective rate, stuck rate, blast radius violations)

This closes the planning loop. Rising corrective rates signal that prompts need more specificity. Recurring blast radius violations signal that scope boundaries need rethinking. The system improves its own planning quality over time.

---

## Design Principles

**Prompts are the product.** Model capability is necessary but not sufficient. A precise prompt produces correct work. A vague prompt produces plausible waste. The strongest available model cannot compensate for ambiguous acceptance criteria.

**Execution framing, not analysis.** Every prompt opens with an imperative directive. Without it, language models default to commentary. "Implement X" produces implementation. "Here is a description of X" produces analysis.

**QA gates, not reports.** Verification verdicts are control signals, not documents. FAIL blocks dependent work. PARTIAL generates corrective prompts. The system acts on its own evaluations. The loop is closed.

**Corrective over rollback.** Failed QA generates fix prompts, not reverts. Work already done has value. A corrective prompt targeting two unmet criteria is cheaper than re-executing the entire original. The system builds forward, never backward.

**Isolation by default.** Every worker operates in a worktree. No shared mutable state. Blast radii enforce scope. Parallel prompts in the same batch are non-overlapping by construction.

**Nothing is lost.** Worker sessions are ephemeral. The system is not. Every observation survives via PR body capture and automated triage. Every QA verdict feeds back to the planner. The system's memory is structural, not dependent on any single session's context.

---

## Operational Boundaries

**What the architect does:**
- Approves execution plans before dispatch begins
- Sets project direction and makes architecture decisions
- Reviews PRs held by merge policy
- Resolves ambiguity the planner flags

**What the architect does not do:**
- Schedule or sequence prompts
- Monitor worker sessions
- Triage observations
- Decide what to do about QA failures

**What triggers architect involvement:**
- Plan approval (before dispatch begins)
- FAIL verdict on a foundational prompt after corrective also fails
- PR held by merge policy (multi-module, public API, PARTIAL verdict)
- Health metric degradation (rising corrective rate, rising stuck rate)

Everything else runs.
