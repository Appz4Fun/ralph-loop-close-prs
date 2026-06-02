## 2026-06-02 - [Optimize _filter_to_still_open_prs GH CLI bottleneck]
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs (e.g. in _filter_to_still_open_prs), running them sequentially causes N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor.map` with a helper wrapper to check states concurrently while preserving original order and gracefully handling `CommandError` exceptions.
