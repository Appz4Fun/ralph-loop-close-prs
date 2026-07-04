## 2025-02-28 - Concurrency for fan-out spawn state checks
**Learning:** Checking the state of PRs sequentially with subprocess calls like `gh pr view` in a supervisor script creates a significant N+1 performance bottleneck when handling multiple PRs. Using `concurrent.futures.ThreadPoolExecutor` mitigates this issue and decreases spawn latencies.
**Action:** When performing N-many slow I/O or subprocess tasks, wrap them in a ThreadPoolExecutor. Always handle exceptions within the worker target to prevent worker crash aborts, and use `executor.map` to preserve evaluation ordering if required.
