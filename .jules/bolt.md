## YYYY-MM-DD - [Title]
**Learning:** [Insight]
**Action:** [How to apply next time]
## 2025-03-09 - Concurrent PR Open State Checking
**Learning:** Subprocess calls to the GitHub CLI ('gh') to check PR status via `_gh_json` sequentially introduces an N+1 delay, significantly bottlenecking the supervisor loop when processing multiple PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to check states concurrently, maintaining the original order with `executor.map` and capturing exceptions in a helper wrapper so they can be handled gracefully in order. Always include a guard for empty collections (`if not items: return []`) before initializing the executor to avoid a `ValueError` with `max_workers=0`.
