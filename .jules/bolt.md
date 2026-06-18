## 2026-06-18 - Concurrent execution of gh commands
**Learning:** Checking states sequentially for multiple PRs causes an N+1 execution bottleneck when invoking the GitHub CLI (`gh`). Using `concurrent.futures.ThreadPoolExecutor` significantly reduces delay.
**Action:** Always map sub-process heavy iterables via `concurrent.futures.ThreadPoolExecutor` in loops, handling missing commands (like 'gh') gracefully.
