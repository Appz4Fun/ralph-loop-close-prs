## 2024-07-03 - ThreadPoolExecutor for GitHub CLI Calls
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs, sequential execution causes an N+1 delay.
**Action:** Use concurrency (`concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential execution delays, taking care to preserve the original order by using `executor.map`, capturing exceptions in a helper wrapper, and safely handling `max_workers` when collections are empty.
