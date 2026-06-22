## 2025-02-28 - Optimize PR state checks with concurrency
**Learning:** Subprocess calls to the GitHub CLI ('gh') sequentially in a loop over multiple PRs causes a significant N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to check multiple PRs concurrently while preserving order and catching exceptions, to improve speed without losing error context.
