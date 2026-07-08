## 2024-07-08 - Optimize PR state checking with ThreadPoolExecutor
**Learning:** Using concurrency for `gh pr view` when checking states for multiple PRs avoids N+1 delays.
**Action:** Use `ThreadPoolExecutor` and `executor.map` with a guard clause to concurrently execute independent subprocess calls.
