## 2024-05-24 - N+1 GitHub API Calls in Multi-Repo Fan-Out
**Learning:** `_list_open_prs` does not use concurrent requests but `_filter_to_still_open_prs` issues one `gh pr view` for every PR sequentially. In a multi-repo supervisor run where there might be many PRs open, this sequential list iteration creates a significant N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to run `_pr_is_still_open` concurrently across PRs to remove the N+1 delay.
