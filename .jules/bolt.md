## 2024-05-18 - Speed up PR open state checks with concurrency
**Learning:** Sequential calls to GitHub CLI (like `gh pr view`) during fan-out PR validation are a severe bottleneck due to N+1 network delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to fetch PR states concurrently, while preserving processing order and accurately propagating `CommandError` for transient failures.
