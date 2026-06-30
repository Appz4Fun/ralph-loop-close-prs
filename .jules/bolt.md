## 2024-06-30 - Concurrent PR state checks
**Learning:** Sequential subprocess calls to the GitHub CLI (gh) create significant N+1 performance bottlenecks.
**Action:** Use concurrent.futures.ThreadPoolExecutor to parallelize independent gh CLI calls, ensuring original order is preserved and handling transient exceptions gracefully.
