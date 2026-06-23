## 2024-05-24 - Optimize PR State Checking with Concurrency
**Learning:** Sequential `gh` CLI subprocess calls (e.g. `gh pr view`) to check states for multiple PRs are a major bottleneck. N+1 sequential execution delays the supervisor fan-out process substantially.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with a helper wrapper and `executor.map` to concurrently execute CLI calls while maintaining order and gracefully handling transient `CommandError`s.
