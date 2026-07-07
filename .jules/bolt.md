## 2024-07-07 - Add concurrent PR checking
**Learning:** Checking PR states in a sequential loop creates an N+1 performance bottleneck, causing delays that scale with the number of open PRs.
**Action:** Use `ThreadPoolExecutor` to run network-bound commands (like checking PR state) concurrently. Ensure ordered output and centralized exception handling in the main thread by mapping the results and handling them sequentially. Added concurrent PR state check in `_filter_to_still_open_prs` to avoid the bottleneck of checking many PRs sequentially.
