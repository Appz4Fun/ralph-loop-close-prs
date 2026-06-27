## 2026-06-27 - [Concurrent Open PR Status Check]
**Learning:** Checking the `gh pr view` for many PRs sequentially in a Python backend script like this one incurs massive N+1 delays.
**Action:** Used `concurrent.futures.ThreadPoolExecutor` via `executor.map` to concurrently execute subprocess calls for checking PR status while still capturing transient network exceptions in original input order.
