## 2026-06-05 - Concurrent PR Check Optimization
**Learning:** Checking PR state sequentially using `gh pr view` in a loop caused N+1 sequential execution delays. This is an architectural bottleneck as each PR check blocks the next. Concurrency mitigates this.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` when performing multiple independent remote operations (like GitHub CLI commands for multiple PRs) to reduce wait time while preserving original structure via `executor.map`.
