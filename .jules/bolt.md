## 2024-05-24 - Avoid N+1 GH CLI calls
**Learning:** Subprocess calls to the GitHub CLI (`gh`) are a significant performance bottleneck. When checking states for multiple PRs (e.g. during fan-out initialization), querying them sequentially creates an N+1 problem that delays supervisor startup.
**Action:** Use concurrency (e.g. `concurrent.futures.ThreadPoolExecutor.map`) to batch independent `gh` CLI checks.
