# 02 — Routing Rules
### Which tool Claude calls for which job
*Triggers: automatic — Claude reads this whenever tool selection is ambiguous*

---

## The Principle

In a multi-tool stack, Claude can guess wrong. Routing rules eliminate the guessing.

Without routing, Claude reaches for whatever tool feels right in the moment.
With routing, the choice is already made. Less guesswork. Cleaner output.

---

## Routing Table

### Vault Operations
- **Primary:** [your MCP server name]
- **Fallback:** [secondary tool]
- **Never use:** copy-paste from vault into chat — defeats the system

### Web Research
- **Primary:** [search tool for your domain]
- **Secondary:** [general search]
- **Documentation lookups:** [Context7 or equivalent]

### Code Execution
- **Primary:** Claude's code interpreter
- **Fallback:** terminal via Claude Code
- **Production code:** [your specific tooling]

### Image Generation
- **Stylized character:** [tool]
- **Photorealistic scene:** [tool]
- **Concept / abstract:** [tool]
- **Quick mockups:** [tool]

### Domain-Specific Routing
- [Domain task 1] → [tool]
- [Domain task 2] → [tool]
- [Domain task 3] → [tool]

---

## How To Use This File

When Claude is about to call a tool and the choice isn't obvious, it should:
1. Check this file
2. Use the primary tool for that task category
3. Fall back to secondary only if primary fails

---

## Update This File When:
- A new tool is added to the stack
- A tool changes behavior or gets deprecated
- You discover a tool was being used for the wrong job

---

## Related

- [[01_session_start]] — the session start that loads this file
- [[../HQ]] — vault map
