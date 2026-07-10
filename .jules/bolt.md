## 2024-05-15 - Concurrent PR state checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a performance bottleneck when checking states for multiple PRs sequentially (N+1 delays).
**Action:** Use concurrent.futures.ThreadPoolExecutor to parallelize independent CLI calls (like checking PR states), preserving order with executor.map and avoiding interleaved logs by handling them sequentially in the main thread.
