## 2024-07-11 - Parallelize gh CLI subprocesses for open PR checking
**Learning:** Checking the open state of many PRs sequentially using gh CLI subprocesses introduces an N+1 performance bottleneck. Subprocess calls are expensive.
**Action:** Use concurrent.futures.ThreadPoolExecutor to parallelize subprocess calls (e.g., gh CLI) when checking state across multiple items, capturing exceptions to ensure the main thread can handle logging safely and sequentially.
