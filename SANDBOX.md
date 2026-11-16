# Sandbox-only changes

This repository is a disconnected rehearsal copy of Mesh-LLM/mesh-llm PR #3107
at `e00b3e7034baba534ee08e25e799b568b1c18747`. It exists to exercise
`release.yml` (Cut) and `release-promote.yml` (Promote) without touching any
production destination. Nothing here is meant to be merged upstream.

Differences from the PR head:

- Removed the 21 workflows that start on their own (`push`, `schedule`,
  `pull_request`, `pull_request_target`, `workflow_run`). Workflows that only
  start by manual dispatch or `workflow_call` are unchanged.
- `release-promote.yml`:
  - the candidate job accepts `michaelneale/mesh-release-lab` instead of
    `Mesh-LLM/mesh-llm`;
  - `dispatch_packaging_release`, `await_packaging_release` and
    `publish_crates` are disabled with `if: ${{ false }}`;
  - `publish_crates_preflight` (dry run, publishes nothing) still runs.

Not tested here, because it is disabled: the mesh-packaging dispatch and its
receipt (images, npm, release assets published from there) and the crates.io
publish.
