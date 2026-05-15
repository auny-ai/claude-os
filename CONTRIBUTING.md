---
title: Contributing to claude-os
description: Guidelines for contributing workflows, documentation, personas, and integrations to the claude-os project. Community-driven development built in public.
category: governance
status: active
tags:
  - contribution
  - community
  - guidelines
  - workflows
  - documentation
---

# Contributing to claude-os 🕷️

Thank you for your interest in contributing to claude-os! This project is built in public, and we're excited to have community contributions that improve the framework for everyone.

## How to Contribute

### 1. **Submit Verified Workflows**
Have you built something with this system? We'd love to see it.

- Create a new file in `workflows/` or `integrations/`
- Document the workflow with:
  - **Problem it solves** - What challenge does this address?
  - **Tools used** - Which AI tools, MCPs, or integrations?
  - **Step-by-step protocol** - Make it reproducible
  - **Real results** - What did you actually achieve?
  - **Time to execute** - How long did it take?

**Example:** If you've automated your newsletter production pipeline, document how you connected NotebookLM → Beehiiv → CapCut with the session protocol.

### 2. **Improve Documentation**
- Clarify existing docs with examples
- Fix broken links or outdated information
- Add diagrams, screenshots, or GIFs to explain concepts
- Translate docs to other languages

### 3. **Expand Persona Templates**
Built a persona that works great? Share it.

- Add to `templates/persona-examples/`
- Include the persona description, behavioral rules, and reading list
- Document what domain/workflow it's optimized for

### 4. **Report Issues & Request Features**
- **Found a bug?** Check existing issues first, then open a new one with:
  - What protocol you were using
  - Expected vs actual behavior
  - Steps to reproduce
  
- **Have a feature idea?** Start a GitHub Discussion to get feedback before opening an issue

### 5. **Contribute to MCPs & Integrations**
Improve MCP configurations or document new tool integrations:
- Create configuration files in `integrations/`
- Include setup guides and troubleshooting
- Link to official docs for the tool

## Contribution Guidelines

### Before You Start
1. Check existing issues and pull requests to avoid duplicates
2. For major changes, open a GitHub Discussion first
3. Test your workflow/protocol in production before submitting

### What We're Looking For
✅ **Reproducible** - Other people can follow your steps  
✅ **Practical** - Real-world results, not theoretical  
✅ **Documented** - Clear, no assumptions  
✅ **Honest** - Include limitations and trade-offs  

### What Won't Be Accepted
❌ Purely theoretical concepts without testing  
❌ Generic AI prompts (this repo focuses on systems, not prompts)  
❌ Advertising or commercial solicitation  
❌ Content that doesn't align with the framework's philosophy  

## Pull Request Process

1. **Fork the repository**
2. **Create a branch** - Use a descriptive name: `add/workflow-ascap-music` or `docs/improve-session-protocol`
3. **Make your changes** - Follow the repo's existing structure and formatting
4. **Test it** - Verify your workflow/documentation works as described
5. **Submit a PR** with:
   - Clear title and description
   - Link to any related issues/discussions
   - Screenshots or examples if applicable
   - Your name/Twitter handle for credit

## Code of Conduct

- Be respectful and constructive
- Give credit where credit is due
- Help each other build better systems
- Share knowledge openly
- No gatekeeping or gatekeeping-adjacent behavior

## Questions?

- **Setup help?** Start a GitHub Discussion under "Q&A"
- **Workflow ideas?** Start a Discussion under "Ideas"
- **Bug reports?** Open an Issue with details

---

## Contributor Recognition

Contributors are recognized in:
- The main README.md under a "Community Workflows" section
- Individual workflow files with your name/GitHub handle
- A CONTRIBUTORS.md file (coming soon)

Let's build this system together. 🚀

*Questions about contributing? Open a Discussion or reach out to [@AunySillyMe](https://x.com/AunySillyMe)*
