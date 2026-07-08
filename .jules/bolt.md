## 2024-05-18 - Concurrent gh cli checks
**Learning:** Sequential shelling out to the `gh` CLI within loops (e.g., checking PR open states during fan-out initialization or supervisor respawns) causes significant N+1 delays, particularly because GitHub CLI starts a new process each time.
**Action:** Always use `concurrent.futures.ThreadPoolExecutor` when performing multiple independent CLI or network operations in a loop. Collect results in worker functions and handle logging sequentially in the main thread to prevent interleaved output.
