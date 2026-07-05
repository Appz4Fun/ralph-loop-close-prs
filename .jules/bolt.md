## 2024-07-05 - Concurrent PR State Checking
**Learning:** The `_filter_to_still_open_prs` function queries GitHub API for each PR sequentially via `gh pr view`, resulting in significant N+1 query latency when there are multiple open PRs.
**Action:** Utilized `concurrent.futures.ThreadPoolExecutor` with `.map()` to make parallel subprocess calls while maintaining output order and sequential logging, significantly reducing waiting time.
