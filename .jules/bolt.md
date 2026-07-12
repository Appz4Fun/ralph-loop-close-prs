## 2024-05-01 - Optimizing N+1 GitHub CLI calls
**Learning:** Checking PR statuses sequentially using external CLI wrappers like `gh pr view` introduces significant N+1 delays.
**Action:** Always use concurrent execution (e.g., ThreadPoolExecutor.map) to parallelize independent CLI subprocess calls, preserving ordering while drastically reducing latency.
