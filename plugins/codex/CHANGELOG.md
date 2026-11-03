# Changelog

## 1.1.1

- `codex:codex-rescue` always runs `task` in the foreground and no longer picks `--background` on its own for long tasks, so it never returns a bare job id.

## 1.1.0

- Bound foreground `task`, `review` and `adversarial-review` with `--max-wait-ms` (default 540000, under Claude Code's 600 s foreground Bash cap). The run executes in the detached worker; a job still active at the bound exits 0 with a stable last line naming the job id and the `status <jobId> --wait --timeout-ms <n>` continuation.
- `codex:codex-rescue` follows that line with `status --wait` until the job is terminal and returns `result`, so it never hands back a bare job id; `--wait` is accepted as a routing flag.
- Stop-review gate bounds its task to its own 15-minute budget.
- Write state and job files atomically so pollers never read a torn file.

## 1.0.7

- Forward model-dependent reasoning efforts to Codex without a fixed allowlist, including `max` and `ultra`.
- Update rescue instructions and runtime help for current effort selection.
- Verify app-server protocol compatibility with Codex CLI `0.159.0`.

## 1.0.0

- Initial version of the Codex plugin for Claude Code
