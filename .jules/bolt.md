## 2025-01-20 - Concurrent Subprocess Executions
**Learning:** Checking PR states sequentially with `gh pr view` creates an N+1 bottleneck. Attempting concurrent execution must handle exceptions carefully to avoid interleaved logging in the main thread and must include a guard clause for empty lists to prevent `ValueError` from `max_workers=0`.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` mapped over a helper function that catches exceptions, then iterate the results sequentially in the main thread to emit logs.
