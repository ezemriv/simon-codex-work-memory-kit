---
title: Global Wiki Log
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: log
tags: [wiki, log]
sources: []
confidence: high
---

# Global Wiki Log

Append a short entry here after every wiki operation. This file is append-only except for routine log rotation if it becomes too large.

When generating this file for a user, write headings, notes, and guidance in the memory language recorded in the global assistant context. Keep file paths and privacy class tokens unchanged.

## Entry Template

```text
## [YYYY-MM-DD] action | Subject

- Summary:
- Pages touched:
- Sources:
```

Actions: `setup`, `ingest`, `update`, `decision`, `query-filed`, `lint`, `split`, `archive`, `delete`.
