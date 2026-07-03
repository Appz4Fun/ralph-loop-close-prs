## 2024-05-23 - ⚡ Bolt: concurrent execution in PR filter
**Learning:** Checking the status of multiple PRs sequentially with `gh pr view` becomes a significant performance bottleneck as the number of open PRs grows. The GitHub CLI can be slow to start and perform the network requests. Using a thread pool to perform these checks concurrently is a big win.
**Action:** When filtering a large number of items requiring individual subprocess calls or network requests, prefer using a `concurrent.futures.ThreadPoolExecutor` mapping to parallelize execution.
