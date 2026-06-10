## 2024-06-10 - Concurrent PR State Checking
**Learning:** Checking PR states using GitHub CLI sequentially causes N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` when performing `_pr_is_still_open` on a list of PR numbers, and add a guard for empty list.
