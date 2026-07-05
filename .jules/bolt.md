## 2024-07-05 - Concurrent GH CLI Calls
**Learning:** Sequential subprocess calls to the GitHub CLI ('gh') for multiple PRs create a significant N+1 performance bottleneck during fan-out initialization.
**Action:** Use `ThreadPoolExecutor.map` to parallelize independent PR state checks while preserving order and sequentially handling logs/exceptions in the main thread.
