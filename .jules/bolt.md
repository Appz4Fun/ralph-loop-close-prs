## 2024-05-24 - Optimize PR State Checks
**Learning:** Sequential GitHub CLI calls are a major bottleneck when fetching state for multiple PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to parallelize independent CLI invocations, reducing N+1 delays.
