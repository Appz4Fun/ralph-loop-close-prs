## 2025-07-07 - Optimize N+1 CLI Bottleneck
**Learning:** Sequential `gh pr view` calls during the startup phase caused a significant N+1 delay bottleneck. Naively putting processes in a `ThreadPoolExecutor` while concurrently invoking un-synchronized logging leads to noisy, interleaved console logs that break formatting.
**Action:** Use a thread pool mapped wrapper to capture states and exceptions from background threads, and only perform logging operations synchronously in the main thread during result aggregation. Ensure to handle `max_workers=0` correctly for empty loops.
