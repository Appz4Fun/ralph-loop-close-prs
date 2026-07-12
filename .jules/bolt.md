## 2024-07-12 - Prevent N+1 query problem with parallel subprocesses for PR checks
**Learning:** Checking the state of multiple PRs in a list sequentially via `_gh_json` leads to N+1 delays, as each check spawns a subprocess call to `gh` CLI which blocks the loop.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to run `_pr_is_still_open` asynchronously. Using a thread pool speeds up list checking and doesn't block the main thread.
