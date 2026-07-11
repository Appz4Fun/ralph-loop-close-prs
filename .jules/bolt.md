## 2025-02-18 - Avoid N+1 bottlenecks with GitHub CLI
**Learning:** Using sequential subprocess calls for the GitHub CLI (`gh`) creates a severe performance bottleneck, especially when iterating over multiple PRs for status checks.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` and `executor.map` to fetch PR states concurrently, while capturing exceptions in a wrapper function to yield them back to the main thread for sequential logging.
