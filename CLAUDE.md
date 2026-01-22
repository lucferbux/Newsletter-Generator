# Claude Code Instructions

This file provides instructions for Claude Code when working with this repository.

## Project Overview

RHOAI Newsletter Generator - A tool for generating Gmail-compatible HTML email newsletters from markdown content for the Red Hat OpenShift AI Dashboard team.

## Agent Instructions

All AI agent instructions (including for Claude Code) are maintained in a single file:

**See [AGENTS.md](./AGENTS.md) for complete instructions.**

The AGENTS.md file contains:
- Gmail compatibility requirements (critical)
- Two-step workflow (release-notes → markdown → newsletter)
- Available newsletter generation actions
- Content types (UI Features vs Platform Improvements)
- Step-by-step workflow for generating newsletters
- HTML component templates
- Best practices and validation checklists
- Error handling guidelines

## Quick Reference

### Key Commands
- `/expand-release-notes` - Transform brief release notes into full markdown
- `/tech-releases` - Generate feature highlights newsletter

### Important Directories
- `release-notes/` - Brief release notes (input for expansion)
- `markdown/` - Full markdown files (source for newsletters)
- `templates/` - HTML newsletter templates
- `newsletters/` - Generated output files
- `docs/` - Documentation and guides

### Critical Rules
1. All HTML must be Gmail-compatible (inline CSS only, table-based layouts)
2. Images must use HTTPS URLs (imgur.com recommended)
3. Maximum email width: 600px
4. Always use the template from `templates/rhoai-template.html`
5. UI Features need screenshots; Platform Improvements use metrics tables
