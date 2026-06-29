## 2024-05-16 - GitHub CLI N+1 Avoidance
**Learning:** Sequential subprocess calls to the GitHub CLI (gh) within a loop create a significant N+1 performance bottleneck, causing large latency during fan-out phases.
**Action:** Use concurrent.futures.ThreadPoolExecutor with executor.map to perform gh calls concurrently, ensuring original ordering is preserved and gracefully wrapping transient failures.
