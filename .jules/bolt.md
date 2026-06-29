## 2024-06-29 - Initializing Bolt Journal
**Learning:** Bolt initialized.
**Action:** Ready to record critical performance learnings.

## 2024-06-29 - Parallelize GitHub CLI Calls in Supervisor
**Learning:** Checking PR statuses sequentially in the supervisor using `gh pr view` via `_pr_is_still_open` can be a significant performance bottleneck due to subprocess execution overhead, especially when checking many PRs at once.
**Action:** Used `concurrent.futures.ThreadPoolExecutor` to check multiple PR statuses concurrently, dramatically reducing the overall delay before child processes spawn. Addressed the `max_workers` zero error memory using a guard clause `if not pr_numbers: return []`.
