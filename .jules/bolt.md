## 2025-02-18 - Optimize PR Status Checks in Fan-Out

**Learning:** Subprocess calls to the GitHub CLI ('gh') via `_gh_json` and `_gh_run_with_retry` are significant performance bottlenecks when checking states for multiple PRs sequentially in a loop.
**Action:** When performing `gh pr view` or similar operations across a collection of PRs, use concurrency (`concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential delays. Ensure that original list order is preserved by using `executor.map`, handle exceptions gracefully by capturing them, and use a guard clause (`if not items: return []`) to prevent a `ValueError` caused by `max_workers=0` when the collection is empty.
