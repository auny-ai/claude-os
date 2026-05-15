---
title: Visual Guide - Quick Start Screenshots
description: Visual walkthrough of the claude-os system with diagrams showing the session protocol flow, vault architecture, and multi-AI orchestration in action.
category: guide
status: active
difficulty: beginner
reading_time: 10 minutes
visual_guide: true
tags:
  - getting-started
  - visual
  - architecture
  - diagrams
---

# Quick Start: Screenshots & Visual Guide

*Visual walkthrough of the claude-os system. Click images to see full size.*

---

## 1. The Session Protocol Flow

The core routing system that powers every Claude session:

```
┌─────────────────────────────────────────────────────────────┐
│                    EVERY SESSION STARTS HERE                │
└─────────────────────────────────────────────────────────────┘
                               ↓
                     1. IDENTIFY (what domain?)
                               ↓
                     2. READ (load relevant files)
                               ↓
                     3. CHECK (pull task status)
                               ↓
                     4. WORK (execute with context)
                               ↓
                     5. UPDATE (mark completed tasks)
                               ↓
                     6. SAVE (write changes to vault)
                               ↓
          ┌─────────────────────────────────────────┐
          │   Next session loads with this context  │
          └─────────────────────────────────────────┘
```

**Key insight:** Nothing is forgotten. Every session builds on the last one.

---

## 2. The Vault-as-Brain Architecture

**Obsidian (local) ←→ MCP ←→ Claude (context loading)**

```
OBSIDIAN VAULT (Single Source of Truth)
│
├─ 🧠 Cognitive Profile
│  └─ Personality, values, decision-making patterns
│
├─ 📝 Content Manual
│  └─ Voice calibration, brand guidelines, output templates
│
├─ 📋 Domain Routing
│  ├─ Content workflows
│  ├─ Music production workflows
│  ├─ Business strategy workflows
│  └─ [Your custom domains]
│
├─ 🎯 Task Tracker
│  └─ Active projects with status (updated every session)
│
├─ 📊 Analytics & Patterns
│  └─ What works, what doesn't, optimization notes
│
└─ 🔗 Tool Integrations
   └─ MCP configs for Linear, Typefully, Beehiiv, Google Drive, etc.
```

**At session start:** Claude reads only what's relevant to your current task. Nothing else.

---

## 3. Multi-AI Stack: Tool-to-Task Mapping

```
                      🎯 YOUR TASK
                           ↓
         ┌─────────────────┼─────────────────┐
         ↓                 ↓                 ↓
    Write & Reason    Deep Research    Real-time Data
         ↓                 ↓                 ↓
      CLAUDE            GEMINI             GROK
    • Vault reading    • Trend analysis   • X/Twitter
    • Strategy         • Long context     • Real-time art
    • Execution        • Fact-checking    • Character work
         ↓                 ↓                 ↓
    ┌─────────────────────────────────────────┐
    │   Secondary opinion? Alternative angle? │
    │         → ChatGPT (when needed)         │
    └─────────────────────────────────────────┘
```

**Result:** No tool is overburdened. Every tool does what it's best at.

---

## 4. Sample Vault Structure (What You'd See in Obsidian)

```
claude-os-vault/
│
├─ 📂 HQ (Navigation Hub)
│  ├─ 📋 Index (master file list)
│  ├─ 📊 Session Log (changes since last session)
│  └─ 🔧 Setup & Config
│
├─ 📂 Protocols
│  ├─ 01_session_start.md
│  ├─ 02_routing_rules.md
│  ├─ 03_content_workflow.md
│  ├─ 04_music_production.md
│  └─ 05_business_strategy.md
│
├─ 📂 Personas
│  ├─ Chief of Staff (strategy + reasoning)
│  ├─ Content Architect (writing + design)
│  ├─ Music Producer (creative direction)
│  └─ [Your custom personas]
│
├─ 📂 Projects
│  ├─ Newsletter (with drafts, analytics)
│  ├─ Music Catalog (ASCAP registration, distribution)
│  ├─ Website (design system, deployment notes)
│  └─ [Active projects]
│
├─ 📂 Knowledge Base
│  ├─ Brand Voice & Tone
│  ├─ Content Guidelines
│  ├─ Music Production Standards
│  ├─ Analytics Patterns
│  └─ Decision-making Frameworks
│
└─ 📂 Integrations
   ├─ Linear config (task sync)
   ├─ Typefully config (content scheduling)
   ├─ Beehiiv config (newsletter publishing)
   └─ [Other tool configs]
```

**Every file is read by Claude at session start if relevant to your current task.**

---

## 5. Example: Content Workflow in Action

**Scenario:** You say "I need a viral post strategy"

```
STEP 1: IDENTIFY
  → User said "viral post" → CONTENT domain

STEP 2: READ
  Claude loads from vault:
  - Content Manual (voice, brand, past successes)
  - Analytics Patterns (what's worked before)
  - Content Routing Protocol
  - Current project status from Linear

STEP 3: CHECK
  Claude queries Linear:
  - Active content projects?
  - Blocked tasks?
  - Recent performance data?

STEP 4: WORK
  Claude creates:
  - Hook analysis based on past patterns
  - 3 angle options with reasoning
  - Platform-specific adaptations
  - Visual brief for design

STEP 5: UPDATE
  Claude updates Linear:
  → "Content strategy: Viral post angles" = DONE
  → Creates task: "Design post cover" (assigns to Claude Design)

STEP 6: SAVE
  Claude updates vault:
  → Session Log: "Generated 3 viral angles for [topic]"
  → Analytics: Noted what resonated with past audience
```

**Result:** Full history. Contextualized suggestions. No starting from zero.

---

## 6. Multi-AI Orchestration Example

**Scenario:** Launching a music release with content about it

```
YOU: "I need a full release package: song, video, post, newsletter."

┌─────────────────────────────────────┐
│  CLAUDE (Chief of Staff)            │
│  → Routes to appropriate tools      │
│  → Manages workflow                 │
│  → Updates vault                    │
└─────────────────────────────────────┘
         ↓
    ┌────┴────┬─────────┬──────────┐
    ↓         ↓         ↓          ↓
  SUNO      CLAUDE   GROK      NOTEBOOKLM
  (Music)   (Strategy) (Art)    (Video)
    ↓         ↓         ↓          ↓
  Song    Post Copy  Character  Voiceover
  Demo    Angles    Art         Script
    ↓         ↓         ↓          ↓
  └────┬─────┴─────┬──────────┐
     ↓           ↓          ↓
  SOUNDBOOST   TYPEFULLY  CAPCUT
  (Master)     (Schedule) (Edit)
     ↓           ↓          ↓
  Master     Queued      Video
  File       Posts       Package
     ↓           ↓          ↓
  DISTROKID  [Publishing]  [Publishing]
     ↓
  Across Spotify, Apple, YouTube, etc.

RESULT: Full release pipeline in 1 session. Coordinated. Documented.
```

---

## 7. Real Output Examples

### Example 1: Music Catalog Registration
- **Input:** "Register my music catalog on ASCAP"
- **Tools:** Claude Cowork + Obsidian vault
- **Output:** 150 songs registered, performing rights tracked, revenue documented
- **Time:** 1 session, autonomous execution

### Example 2: Website Launch
- **Input:** "Build my portfolio site"
- **Tools:** Claude Code + design system from vault
- **Output:** aunysillyme.com live with full branding
- **Time:** Direction → Build → Ship in one workflow

### Example 3: Content to Video Pipeline
- **Input:** "Turn my newsletter into a video series"
- **Tools:** NotebookLM (voiceover) → Beehiiv (extract) → CapCut (edit)
- **Output:** 3 cinematic video overviews ready to publish
- **Time:** Content → Video in coordinated workflow

---

## 8. Getting Started: What You Need

1. **Obsidian** (free) - Your local vault
2. **Claude Projects** (free in Claude.ai, Pro for capabilities)
3. **One MCP** to start - We recommend Obsidian
4. **The templates in this repo** - Copy `/templates/vault-skeleton/` to your Obsidian

**Time to setup:** 30 minutes

---

## 9. Key Concepts at a Glance

| Concept | What It Is | Why It Matters |
|---------|-----------|----------------|
| **Session Protocol** | 6-step routing system | Every session is contextual, never generic |
| **Vault** | Obsidian + MCP connection | Single source of truth for all tools |
| **Domain Routing** | Different protocols for different tasks | Content work ≠ music work ≠ strategy work |
| **Persona** | Named role with job description | Clear expectations, consistent output |
| **Multi-AI Stack** | Right tool for right job | No tool overburdened, everything optimized |
| **Task Tracking** | Updated live in session | Nothing falls through cracks |

---

## 10. Next Steps

1. **Read** `/session-protocol/01_session_start_protocol.md` - understand the routing
2. **Copy** `/templates/vault-skeleton/` into Obsidian
3. **Connect** your first MCP (start with Obsidian)
4. **Build** your first domain-specific protocol
5. **Document** what works (share in discussions!)

---

*Questions? Start a GitHub Discussion or reach out [@AunySillyMe](https://x.com/AunySillyMe)*
