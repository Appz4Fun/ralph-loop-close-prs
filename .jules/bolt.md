## 2026-06-16 - [Concurrent PR status checking]
**Learning:** Checking states sequentially for multiple PRs causes N+1 execution delays as each requires a synchronous gh CLI subprocess call.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` and `executor.map` with wrapper functions to maintain order and effectively hide subprocess latency when checking multiple PR states.