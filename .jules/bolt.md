## 2024-05-18 - Optimize PR state checking with concurrency
**Learning:** Checking PR state sequentially for large lists using `gh pr view` introduces significant N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` and `executor.map` for concurrent execution, avoiding max_workers=0 by checking if the list is empty, and ensuring logs are processed sequentially in the main thread to avoid interleaving.
