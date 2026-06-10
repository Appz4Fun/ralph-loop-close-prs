## 2026-06-10 - Concurrently fetching PR states
**Learning:** Subprocess calls to the GitHub CLI ('gh') to check states sequentially, like in `_filter_to_still_open_prs`, are a performance bottleneck because they invoke N separate processes.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform independent external CLI commands (like fetching PR states) concurrently. Ensure original output order is preserved by using `executor.map` and correctly wrap errors in a `Tuple` so exceptions are not silently discarded, and a guard against empty input is added.
