## 2024-05-24 - Speed up fan-out PR state checks
**Learning:** Sequential subprocess calls to the GitHub CLI (`gh`) are a significant performance bottleneck. When checking states for multiple PRs (e.g. `_filter_to_still_open_prs`), the N+1 sequential execution delays add up quickly.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential execution delays. Ensure that the original order is preserved by using `executor.map`, and capture exceptions (like `CommandError`) in a helper wrapper so they can be yielded and handled gracefully in order.
