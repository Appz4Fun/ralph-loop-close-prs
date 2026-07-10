## 2024-07-10 - Concurrency for GitHub CLI calls
**Learning:** Checking PR statuses one by one with `gh pr view` creates an N+1 delay bottleneck. Sequential subprocess calls can be slow when large lists of PRs are involved.
**Action:** When making multiple independent CLI/network calls, use a `ThreadPoolExecutor` to execute them concurrently, being mindful of exception handling to maintain original failure behaviors. Guard dynamically calculated `max_workers` to avoid crashes on empty input lists.
