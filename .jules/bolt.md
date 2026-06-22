## 2026-06-21 - Concurrent GitHub CLI Calls
**Learning:** Sequential subprocess calls to `gh` for fetching state (like PR open status) cause N+1 delays, acting as a performance bottleneck when checking multiple PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with a guard for empty iterables (`if not items: return []`) and bounded `max_workers` to parallelize independent external API queries, yielding results preserving original order to speed up execution.
