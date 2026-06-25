## 2024-05-24 - N+1 API Calls on Fan-out PR State Validation
**Learning:** Checking the validity of PRs sequentially using `gh pr view` via `_pr_is_still_open` inside `_filter_to_still_open_prs` or similar logic results in N+1 subprocess calls to the GitHub CLI. This is a severe performance bottleneck during fan-out supervisor startup/respawning when there are many PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` mapped execution to parallelise independent subprocess checks when gathering state for multiple items to avoid blocking delays.
