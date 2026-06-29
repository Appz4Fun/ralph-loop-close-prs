## 2024-06-29 - Parallelize PR State Verification
**Learning:** Sequential subprocess calls to the GitHub CLI (`gh`) during PR state checks cause significant N+1 delays, acting as a performance bottleneck.
**Action:** Used `concurrent.futures.ThreadPoolExecutor` with `executor.map` to process PR state checks concurrently while maintaining their original order and gracefully handling `CommandError` via a helper wrapper function. Added a guard clause `if not pr_numbers: return []` to prevent `ValueError` from `max_workers=0`.
