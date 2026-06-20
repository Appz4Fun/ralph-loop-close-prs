## 2026-06-20 - [Performance Optimization]
**Learning:** Checking state for multiple PRs without concurrency leads to N+1 sequential execution delays.
**Action:** When gathering data for multiple operations that run via subprocesses, use `concurrent.futures.ThreadPoolExecutor` to speed it up.
