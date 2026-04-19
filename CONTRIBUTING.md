# Contributing

This repo is the GitHub profile README for **forkwright**. It's a tiny
docs-only repo, but it follows the same contributor flow as the rest of
the fleet.

## Forge-native PR flow (primary)

The authoritative copy of this repo lives on the self-hosted kanon
forge at `http://kanon.lan/forkwright/forkwright`.

1. Push a feature branch to the forge:
   ```
   git push origin <branch>
   ```
   (`origin` points at `http://127.0.0.1:7878/forkwright/forkwright.git`
   — the forge at `kanon.lan`.)

2. Open a PR through the forge:
   ```
   kanon pr open <branch> --full-name forkwright/forkwright --title "..."
   ```
   or via the stoa UI at `http://kanon.lan/prs/forkwright/forkwright`.

3. Review and approve via stoa. The merge button is gated on CI Pass
   + verifier Ok + a `Gate-Passed: kanon <version>` trailer on the
   merge commit. Docs-only pushes run the `checkout-ok` no-op stage
   from `.kanon-ci.toml` (there is no Rust workspace to build).

4. Merge locally:
   ```
   kanon pr merge <N> --full-name forkwright/forkwright --strategy squash
   ```
   (or squash via the stoa UI). Post-merge, the GitHub mirror picks
   up `main` within the mirror worker's next tick (≤ 60s, often <10s).

## GitHub mirror (secondary)

The forge auto-mirrors `refs/heads/main` + tags to
`https://github.com/forkwright/forkwright`. External contributors can
still open PRs on GitHub; the forge's inbound PR-sync pulls them in as
forge `PrRecord` entries so the review surface stays unified.

For fleet-internal work, prefer the forge flow above — the GitHub
mirror is for external discoverability, not primary authoring.

## Escape hatch

If the forge is unreachable:

1. Push to the GitHub mirror directly: `git push github <branch>`.
2. Open a GitHub PR the usual way.
3. When the forge comes back, the mirror worker will ingest the
   GitHub PR into a `PrRecord` on the forge side for review /
   continuity.

## Cutover lineage

This CONTRIBUTING.md landed as the forkwright Phase 05e cutover
(2026-04-19), the fifth fleet repo to adopt forge-native PRs after
dioptron (2026-04-19). Remaining cutovers: harmonia, akroasis,
thumos, hamma, aletheia (aletheia last per
`projects/kanon/phases/05-forge-prs/subphases/05e-cutover/PLAN.md`).
