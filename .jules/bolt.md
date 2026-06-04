## 2024-06-03 - Concurrent fan-out
**Learning:** Sequential Github API calls checking `_pr_is_still_open` can be a significant performance bottleneck during fan-out.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to perform checking operations concurrently while preserving original order and gracefully handling `CommandError`s.
