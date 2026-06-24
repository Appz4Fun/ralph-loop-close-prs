## 2025-02-23 - Concurrent GitHub CLI Calls
**Learning:** Checking states for multiple PRs via sequential `gh` CLI subprocess calls (e.g., `_pr_is_still_open` inside a loop) creates a significant N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to run independent `gh` CLI calls concurrently, ensuring an empty list guard is present to avoid `ValueError` with `max_workers=0`, and handle exceptions inside a mapping wrapper.
