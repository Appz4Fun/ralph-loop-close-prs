## 2024-05-24 - Optimize PR State Check
**Learning:** Sequential subprocess calls to the GitHub CLI ('gh') for PR state checks introduce significant delays. Using concurrent execution mitigates this N+1 bottleneck.
**Action:** Use concurrent.futures.ThreadPoolExecutor for operations like checking PR state that rely heavily on slow subprocess calls while handling exceptions per item.