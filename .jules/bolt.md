## 2024-10-24 - Concurrent GitHub PR Checks
**Learning:** Sequential subprocess calls to the GitHub CLI (gh) introduce an N+1 delay bottleneck.
**Action:** Use ThreadPoolExecutor to run these calls concurrently while maintaining sequential logging to prevent interleaved output.
