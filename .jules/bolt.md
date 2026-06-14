## 2024-05-18 - Concurrent `gh pr view` to avoid N+1 query problems in fan-out loops
**Learning:** Checking PR state sequentially (`for pr in pr_numbers: _pr_is_still_open(pr)`) using external subprocesses (`gh`) creates a severe performance bottleneck (N+1 query problem) on the fan-out supervisor startup or respawn loop, especially for many PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to execute multiple `gh pr view` operations concurrently, dramatically speeding up the filtering phase. Make sure to preserve order and capture exceptions so they can be processed appropriately.
