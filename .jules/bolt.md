## 2024-05-18 - Concurrent fan-out state checks
**Learning:** Using sequential `gh pr view` for a batch of PRs introduces severe N+1 latency for the supervisor loop on startup. Using thread pools with `executor.map` and capturing exceptions in a wrapper reduces latency significantly without altering ordering or error handling semantics.
**Action:** Use thread pooling for batch GitHub CLI checks whenever checking state for multiple PRs.
