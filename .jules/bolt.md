## 2024-06-11 - Optimize _filter_to_still_open_prs with concurrency
**Learning:** Checking PR statuses one by one using subprocess calls to the `gh` CLI introduces a significant N+1 sequential bottleneck, leading to dramatic overall performance degradation as the number of PRs grows. `gh pr view` overhead dominates runtime.
**Action:** Always use `concurrent.futures.ThreadPoolExecutor` when performing multiple sequential calls to the `gh` CLI over a list of items to execute them concurrently, taking care to map over items and wrap calls to properly catch and surface exceptions.
