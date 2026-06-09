## 2024-05-18 - [CLI Fan-out Concurrency Optimization]
**Learning:** The CLI fan-out logic queries the open state for multiple PRs using sequential `gh pr view` subprocess calls (`_pr_is_still_open`), which introduces a significant performance bottleneck due to sequential execution.
**Action:** When performing multiple independent I/O or subprocess tasks like checking PR states, use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) with mapped execution to avoid N+1 delays while preserving original order. Ensure empty iterables are guarded so `max_workers` doesn't evaluate to `0`.
