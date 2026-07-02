## 2024-07-01 - Parallelize PR state filtering
**Learning:** Subprocess calls to the GitHub CLI ('gh') via _gh_json and _pr_is_still_open create significant N+1 sequential execution delays.
**Action:** Use concurrent.futures.ThreadPoolExecutor to parallelize independent network calls, mapping helpers that gracefully capture and return exceptions.
