# 01 — Session Start Protocol
### What Claude reads + checks at the start of every session
*Triggers: automatic at start of every chat / "session start" / "load context"*

---

## Read In This Order Every Session

| STEP | FILE | WHY |
|---|---|---|
| 1 | `Session_Log.md` | What changed in other chats since last session |
| 2 | `HQ.md` | Vault map — what files exist and how to find them |
| 3 | Task-specific protocol | Loaded based on what the user asks for first |

---

## Then Check (If Applicable)

- Task tracker (Linear / Things / GitHub Issues / whatever)
- Recently modified files in folders relevant to the task
- Any open drafts in the writing/coding tool of choice

---

## Then Act

Only after Steps 1–3 are complete should Claude begin the actual work.

---

## What This Replaces

Without this protocol:
- Every session starts cold
- Conventions get forgotten
- The same context gets pasted in over and over
- Changes from one chat aren't visible to the next

With this protocol:
- Every session starts with the full picture
- Conventions persist
- Context loads automatically
- Cross-chat continuity works

---

## Customize This For Your Vault

The skeleton above works for most setups. Customize by:

1. Adding domain-specific reads (e.g. "Read content_manual.md for content sessions")
2. Adding tool-specific checks (e.g. "Pull last 7 days analytics if it's a content session")
3. Adding routing logic ("If user mentions X, load Y protocol")

A 20-line session start protocol replaces 50+ lines of repeated "remember to..." instructions you'd otherwise type into CLAUDE.md.

---

## Related

- [[02_routing_rules]] — which tool to call when
- [[../HQ]] — the vault map this protocol loads
