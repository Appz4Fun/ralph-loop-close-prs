## 2024-05-19 - Concurrent API fetching in _gh_json
**Learning:** _gh_json executes github cli sequentially which could be parallelized, but the tool is largely designed as simple wrappers around the gh cli, making single invocations slow. But maybe there are places where `_gh_json` is called in a loop, for example `_list_open_prs`. Let's check!
**Action:** Always look for O(n) gh api fetch patterns.
## 2024-05-19 - Concurrent API fetching in _filter_to_still_open_prs
**Learning:** `_filter_to_still_open_prs` fetches PR states sequentially, making `_filter_to_still_open_prs` N+1 sequential execution. I will refactor it to run in parallel, using `concurrent.futures.ThreadPoolExecutor`.
**Action:** Use ThreadPoolExecutor to check states in parallel. But wait, I need to make sure order is preserved. `executor.map` will preserve the original order. I also need to make sure to handle the exception, as map will raise exception when generating the result from the iterator. So I can wrap the `_pr_is_still_open` function in a helper that catches the error and returns a tuple.
## 2024-05-19 - Concurrent API fetching in _filter_to_still_open_prs
**Learning:** `_filter_to_still_open_prs` fetches PR states sequentially, making `_filter_to_still_open_prs` N+1 sequential execution. I will refactor it to run in parallel, using `concurrent.futures.ThreadPoolExecutor`.
**Action:** Use ThreadPoolExecutor to check states in parallel. But wait, I need to make sure order is preserved. `executor.map` will preserve the original order. I also need to make sure to handle the exception, as map will raise exception when generating the result from the iterator. So I can wrap the `_pr_is_still_open` function in a helper that catches the error and returns a tuple.
