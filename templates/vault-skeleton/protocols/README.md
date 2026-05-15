---
title: Protocols — Session Management & Routing
description: Every protocol Claude uses to work inside the vault. Session start protocols, routing rules, and domain-specific workflows.
category: framework
status: active
section: templates
tags:
  - protocols
  - session-management
  - routing
  - workflows
---

# 📐 Protocols

*Every protocol Claude uses to work inside this vault. Every session loads one or more of these.*

---

## Files

| FILE | PURPOSE |
|---|---|
| [[01_session_start]] | What Claude reads + checks at the start of every session |
| [[02_routing_rules]] | Which tool to call for which job |
| [[03_task_specific_protocol]] | Your domain-specific workflow (rename to fit) |

---

## The Session Loop

```
1. READ    → Session_Log (changes since last chat)
2. READ    → HQ (vault map)
3. LOAD    → task-specific protocol based on what user wants
4. CHECK   → task tracker for open issues (if applicable)
5. WORK    → execute
6. SAVE    → log changes to Session_Log
```

This loop runs every session. Steps 1, 2, and 6 are non-negotiable.

---

*Vault first. Then act.*
