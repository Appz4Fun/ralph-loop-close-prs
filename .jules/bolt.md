## 2024-06-27 - Optimize PR open state checks with concurrency
**Learning:** Sequential network-bound checks (like fetching states for multiple PRs via gh CLI) cause significant N+1 delays.
**Action:** Use concurrent.futures.ThreadPoolExecutor with a wrapper function to parallelize these checks while preserving order and gracefully handling exceptions. Ensure a guard clause `if not items: return []` is used to prevent `max_workers=0` ValueError.
