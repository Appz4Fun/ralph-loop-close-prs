## 2024-06-13 - [Concurrency for gh PR list]
**Learning:** Subprocess calls to the GitHub CLI (`gh`), specifically during the N+1 sequential execution of `_pr_is_still_open` across many PRs, represent a significant performance bottleneck due to process instantiation overhead and network latency.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` and a helper wrapper to execute independent `gh` subprocess calls concurrently, ensuring a guard clause handles empty lists and exceptions are captured correctly without breaking the original order.
