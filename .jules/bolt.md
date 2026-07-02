## 2024-05-24 - Concurrency for GitHub CLI calls
**Learning:** Subprocess calls to the GitHub CLI (`gh`) are a significant bottleneck when filtering many PRs sequentially.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to execute `gh pr view` for multiple PRs concurrently to reduce overall wait time, being careful to maintain PR order and handle empty collections correctly.
