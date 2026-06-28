## 2024-05-24 - Concurrent GitHub CLI Checks
**Learning:** Sequential GitHub CLI subprocess calls (like `gh pr view` for multiple PRs) create a significant N+1 performance bottleneck during loop startup.
**Action:** When filtering or gathering state for a collection of PRs, use `concurrent.futures.ThreadPoolExecutor` with a dynamic `max_workers` guard (to avoid ValueError on empty collections) and map over a wrapper that catches and returns exceptions to gracefully preserve deterministic ordering and error handling.
