## 2024-05-24 - Speed up PR state checking
**Learning:** Sequential N+1 network requests (like `gh pr view` on an array of PRs) cause significant performance bottlenecks in supervisors.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to fetch states concurrently. Ensure `executor.map` is used to preserve ordering, and catch/yield exceptions to handle them sequentially without breaking the concurrent flow. Ensure max_workers > 0 by checking for an empty array early.
