## 2024-06-25 - Use concurrency for sequential gh subprocess calls
**Learning:** Checking the state of multiple PRs by sequentially spawning `gh pr view` subprocesses (`_pr_is_still_open`) results in extreme latency due to the overhead of external API network calls and process creation delays (the classic N+1 problem).
**Action:** Always use `concurrent.futures.ThreadPoolExecutor` when dispatching multiple independent subprocess calls or API requests to external services, and ensure exceptions are safely caught in the concurrent mapper before yielding back to the main sequential flow.
