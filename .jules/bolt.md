## 2025-02-12 - [Concurrent GitHub API Calls in fan-out supervisor]
**Learning:** Making sequential `gh pr view` calls for each open PR created an N+1 performance bottleneck. Subprocess calls to the GitHub CLI are relatively slow and blocking.
**Action:** Always use `concurrent.futures.ThreadPoolExecutor` when performing multiple independent `gh` CLI checks across different entities, ensuring `executor.map` is used to maintain original PR ordering and that a guard clause prevents `max_workers=0` on empty lists.
