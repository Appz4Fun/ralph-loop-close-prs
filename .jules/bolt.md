## 2026-07-04 - N+1 Delay with GitHub CLI Processes
**Learning:** Sequential subprocess calls to the `gh` CLI (e.g., checking PR state via `gh pr view`) cause significant N+1 delays in the fan-out loop, heavily bottling up performance when many PRs are present.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` when performing batch CLI interactions that spawn network-bound CLI processes, ensuring to handle exceptions and preserve output order without interleaved logs.
