## 2024-10-25 - Concurrent GH CLI Operations
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs, sequential execution causes severe N+1 delays.
**Action:** When performing bulk operations like checking PR status, use `concurrent.futures.ThreadPoolExecutor` and `.map` to fetch data concurrently while preserving order, which drastically reduces total blocking time.
