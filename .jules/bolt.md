## 2024-06-14 - Concurrent GitHub PR checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') sequentially can be a performance bottleneck when checking multiple PRs.
**Action:** When performing independent `gh` operations across multiple items (like checking PR states), use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to run them concurrently while preserving order, ensuring proper exception handling and empty list guarding.
