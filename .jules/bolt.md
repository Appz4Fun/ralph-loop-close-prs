## 2024-05-24 - Parallelized GitHub API PR Queries
**Learning:** Checking PR statuses sequentially causes N+1 delays, acting as a performance bottleneck when there are many PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to perform the `gh pr view` commands concurrently, avoiding N+1 delays while keeping results sequentially ordered and properly logging exceptions from threads. Always remember to add a guard block for empty lists (`if not list: return []`) before passing collection lengths to `max_workers` to prevent `ValueError` due to zero workers.
