# Connecting Grok to Claude via MCP
### How to give Claude live X search and Grok's DeepSearch — 
### and why it changes content sessions completely

---

## What This Unlocks

Claude's built-in web search is good.
It doesn't search X natively.

Grok does two things nobody else does:

**1. Real-time X post search**
Search actual posts on X by keyword, handle, or date range.
Right now. Live. With citations.
Not web search that happens to include some tweets.
Actual X post search.

**2. DeepSearch**
Web research that's significantly more current
than standard search tools.

When Grok is connected to Claude via MCP,
Claude can call both of those tools
directly inside a session —
without switching apps, without copying anything.

**What this looks like in a content session:**
```
"Write me 5 posts on AI agents"
→ Claude reads your content pillars from the vault
→ Claude calls Grok's x_search for what's trending
on X about AI agents right now
→ Claude writes posts in your voice,
timed to live conversation
```
That combination — vault context + live X data + 
your voice — is not possible any other way.

---

## What You Need

- Claude Desktop (desktop app, not browser)
- An xAI API key (free credits available)
- 15 minutes

---

## Step 1 — Get Your xAI API Key

The Grok MCP requires an xAI API key.
This is separate from your Grok subscription on X.

**The good news: free credits are generous.**

xAI gives every developer up to $175/month free:
- $25 free on signup
- $150/month extra if you enable data sharing
  in your console settings

For a few X searches per content session,
the free credits cover months of usage.

**To get access:**
1. Go to **console.x.ai**
2. Sign up or log in
   (you may already have an account if you use Grok on X)
3. Go to **API Keys** → create a new key
4. Go to **Settings** → **Data Sharing** → enable it
   to unlock the $150/month free credits
5. Copy your API key — you'll need it in Step 3

---

## Step 2 — Create The Install Script

Open a text editor (TextEdit on Mac, Notepad on Windows).
Create a new file and paste this:

```bash
#!/bin/bash
set -e

echo "Installing Grok MCP server..."

# Install the Grok MCP package
npm install -g @xai/grok-mcp 2>/dev/null || \
npx -y @modelcontextprotocol/create-server grok-server

# Get Claude Desktop config location
if [[ "$OSTYPE" == "darwin"* ]]; then
    CONFIG_DIR="$HOME/Library/Application Support/Claude"
else
    CONFIG_DIR="$APPDATA/Claude"
fi

CONFIG_FILE="$CONFIG_DIR/claude_desktop_config.json"

echo ""
echo "Paste your xAI API key when prompted."
echo "It will not be saved to any file or chat."
read -s -p "xAI API Key: " XAI_KEY
echo ""

# Add Grok MCP to Claude Desktop config
python3 - <<EOF
import json, os

config_path = "$CONFIG_FILE"
xai_key = "$XAI_KEY"

if os.path.exists(config_path):
    with open(config_path, 'r') as f:
        config = json.load(f)
else:
    config = {}

if 'mcpServers' not in config:
    config['mcpServers'] = {}

config['mcpServers']['grok'] = {
    "command": "npx",
    "args": ["-y", "@xai/grok-mcp"],
    "env": {
        "XAI_API_KEY": xai_key
    }
}

with open(config_path, 'w') as f:
    json.dump(config, f, indent=2)

print("Grok MCP added to Claude Desktop config.")
EOF

echo ""
echo "Done. Now:"
echo "1. Press Cmd+Q to fully quit Claude Desktop"
echo "2. Reopen Claude Desktop"
echo "3. Go to Settings → Developer"
echo "4. You should see 'grok' in your MCP servers list"
```

Save the file as `install-grok-mcp.sh` on your Desktop.

---

## Step 3 — Run The Script

Open Terminal (Mac: search "Terminal" in Spotlight).

Run:
```bash
bash ~/Desktop/install-grok-mcp.sh
```

When prompted, paste your xAI API key.
Hit Enter.

The key is entered directly in Terminal —
it never touches a file or a chat.

---

## Step 4 — Restart Claude Desktop

**Cmd+Q** to fully quit Claude Desktop.
Not just close the window — fully quit.

Reopen Claude Desktop.

Go to **Settings** → **Developer** →
you should see `grok` in your MCP servers list
alongside any other servers you have running
(like `auny-vault` if you have Obsidian connected).

---

## Step 5 — Test The Connection

Open a new Claude conversation and type:
```
Use Grok's x_search to find what's trending
on X about AI workflows right now.
```
Claude should call the Grok MCP,
run an X search, and return live results with citations.

If it works — you're live. 🕷️

---

## Step 6 — Update Your Session Protocol

Connection confirmed. Now tell Claude when and how to use it.

Add this to your Claude Project instructions:
```
RESEARCH PROTOCOL:
When running content research, use Grok MCP x_search
for live X trend data — not general web search.
Search within my content pillars only:

AI workflows and tools
Creator systems and monetization
Music and independent artist content
Personal brand and identity

A topic trending on X doesn't automatically mean
it's relevant. Cross-reference against my content
pillars before including in content direction.
State what you searched and what you found
before writing anything.
```
**The pillar filter is critical.**
Without it, Claude will surface whatever is trending —
not what's relevant to your specific content strategy.
Trending and relevant are not the same thing.

---

## What The Automated Session Looks Like

With Grok MCP connected and the protocol in place,
a content session runs like this automatically:
```
1. Pull published posts (last 30)       ← Typefully MCP
2. Pull scheduled queue                 ← Typefully MCP
3. Pull analytics (last 7 days)         ← Typefully MCP
4. Run research (Grok MCP - x_search)   ← Grok MCP
5. Apply recency weighting
6. Read signals
7. State content direction
8. Cross-reference queue
9. Verify format rotation
10. Write
```
Steps 1-4 happen automatically via MCP
before a single post gets written.
No prompting required.
Built into the session protocol.

---

## The Three Tools Available

When you install the Grok MCP you get access to:

| TOOL | WHAT IT DOES | WHEN TO USE |
|------|-------------|-------------|
| `x_search` | Live X post search by keyword, handle, date | Content research, trend awareness |
| `web_search` | Grok's DeepSearch — more current than standard | Deep research, current events |
| `chat_completion` | Call Grok directly as a model | X-native reasoning, 2M token context |

For content sessions, `x_search` is the primary tool.
`web_search` adds depth when a topic needs it.
`chat_completion` is for tasks that benefit from
Grok's X-native knowledge or larger context window.

---

## The Honest Limitation

Grok's MCP support is still early.

The full bidirectional read/write vault experience
(like the Obsidian MCP) isn't there yet with Grok.
The X search and DeepSearch tools work reliably.
`chat_completion` via MCP is functional but evolving.

The X search angle alone makes this worth setting up.
There is no other way to get live X post data
directly inside a Claude session.

---

## What This Adds To The Stack

Before Grok MCP:
Claude researches using general web search.
It finds articles about what was trending.
Not what's trending right now on X.

After Grok MCP:
Claude searches X directly.
It finds posts from the last hour.
It writes content timed to live conversation —
not yesterday's news.

For anyone creating content for X specifically,
this is the highest-leverage MCP addition
to the stack after Obsidian.

---

## Related Files

- [Session Start Protocol](../session-protocol/01_session_start_protocol.md)
  — how Grok MCP fits into the full session loop
- [Tool-to-Task Mapping](../multi-ai-stack/02_tool_to_task_mapping.md)
  — where Grok sits in the full stack
- [Vault Architecture](../vault-architecture/01_obsidian_structure.md)
  — the Obsidian MCP setup this builds on

---

*auny-ai/claude-os — a multi-AI operating system being built in public.*
*Learning as I go. Sharing it all for you.* 🕷️
