## 2025-02-14 - ThreadPoolExecutor for concurrent GitHub API calls
**Learning:** Checking PR state loops over GitHub CLI subprocesses, leading to a N+1 query bottleneck. Concurrency eliminates this problem while returning in mapping order.
**Action:** When evaluating multiple states requiring individual subprocess `gh` calls in a map loop, use `concurrent.futures.ThreadPoolExecutor.map` with appropriate max worker guards.
