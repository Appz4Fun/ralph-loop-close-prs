## 2026-06-22 - Optimize filter_to_still_open_prs with Concurrent ThreadPoolExecutor
**Learning:** Sequential calls to the GitHub CLI ('gh') via `_gh_json` in a loop represent a significant performance bottleneck due to subprocess execution overhead for multiple checks (N+1 delay pattern).
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to fetch PR statuses concurrently, significantly reducing wait times for PR batch processing. Always include a guard clause for empty PR lists to avoid triggering ValueError on dynamic `max_workers=0` conditions.
