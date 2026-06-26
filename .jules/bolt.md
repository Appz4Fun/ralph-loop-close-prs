## 2024-06-26 - Concurrent PR state checks
**Learning:** Checking PR state sequentially using `_pr_is_still_open` with subprocess calls to `gh pr view` creates a severe bottleneck during fan-out, especially when polling multiple PRs. Sequential N+1 execution of slow external CLI commands is an anti-pattern.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to run CLI-dependent checks in parallel, significantly reducing the time spent determining which PRs to spawn workers for. Always guard the executor initialization against empty collections (`if not collection: return`).
