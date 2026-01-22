# Usage Guide - RHOAI Newsletter Generator

Complete guide to creating professional HTML newsletters from markdown content using AI assistance.

---

## Table of Contents

1. [Getting Started](#getting-started)
2. [Workflow Overview](#workflow-overview)
3. [Writing Release Notes](#writing-release-notes)
4. [Content Types](#content-types)
5. [Using AI Actions](#using-ai-actions)
6. [Template Customization](#template-customization)
7. [Previewing Newsletters](#previewing-newsletters)
8. [Image Management](#image-management)
9. [Troubleshooting](#troubleshooting)
10. [Best Practices](#best-practices)

---

## Getting Started

### Setup Verification

Ensure your project structure is correct:

```
Newsletter/
├── AGENTS.md                        ✓ AI agent instructions
├── CLAUDE.md                        ✓ Claude Code instructions
├── templates/rhoai-template.html    ✓ HTML template
├── release-notes/                   ✓ Brief release notes
├── markdown/                        ✓ Full markdown content
├── newsletters/                     ✓ Generated HTML output
└── docs/                            ✓ Documentation
```

### Choose Your AI Assistant

This project works with:
- **Claude Code** (CLI / VS Code)
- **GitHub Copilot Chat** (VS Code / Cursor)
- **Claude** (Anthropic)
- Any AI assistant that can read project files

---

## Workflow Overview

The newsletter generation follows a two-step workflow:

```
release-notes/*.md → /expand-release-notes → markdown/*.md → /tech-releases → newsletters/*.html
```

### Step 1: Write Brief Release Notes
Create concise release notes in `release-notes/` folder with key features and metrics.

### Step 2: Expand to Full Markdown
Use `/expand-release-notes` to transform brief notes into full newsletter content.

### Step 3: Generate HTML Newsletter
Use `/tech-releases` to generate the final Gmail-compatible HTML.

---

## Writing Release Notes

### Create Your Release Notes File

Save brief release notes in the `release-notes/` folder:

```bash
touch release-notes/rhoai-2.36-sprint.md
```

### Structure Your Content

Use this format for release notes:

```markdown
# RHOAI 2.36 Sprint Release Notes

**Sprint:** December 2025
**Version:** 2.36.0
**Team:** Dashboard Platform Team

---

## UI Features

### Feature Name
Brief description of what it does.

**Screenshot:** https://i.imgur.com/PLACEHOLDER.png

- Key capability 1
- Key capability 2
- Key capability 3

---

## Platform Improvements

### Improvement Name
Description of the optimization.

- Metric 1: Before → After (X% improvement)
- Metric 2: Before → After (Y% improvement)

---

## Bug Fixes

- Fixed: Issue description
- Fixed: Another issue

---

## Known Issues

- Known issue and workaround
```

---

## Content Types

### UI Features (with screenshots)

Features that have visible UI changes should include:
- Screenshot URL (imgur.com recommended)
- Brief feature bullets
- User-facing capabilities

**Example:**
```markdown
### Model Comparison View
Compare multiple models side-by-side with unified metrics display.

**Screenshot:** https://i.imgur.com/ABC123.png

- Compare up to 4 models simultaneously
- See performance metrics in unified view
- Export comparison results as PDF
```

### Platform Improvements (metrics-based)

Backend improvements and performance gains:
- No screenshot required
- Before/After metrics
- Percentage improvements

**Example:**
```markdown
### API Response Time Optimization
Optimized backend queries and caching layer.

- Dashboard load time: 2.1s → 0.8s (62% faster)
- Model list API: 450ms → 120ms (73% faster)
- Search queries: 800ms → 200ms (75% faster)
```

---

## Using AI Actions

### `/expand-release-notes`

**Purpose:** Transform brief release notes into full newsletter-ready markdown.

**Full Example:**

```
/expand-release-notes

Expand release notes to full newsletter markdown.
Source: release-notes/rhoai-2.36-sprint.md
Output: markdown/rhoai-2.36-features.md

Transform brief feature descriptions into full sections with:
- What You Can Do (checkmarks)
- How to Use It (numbered steps)
- Perfect For (use cases)
```

**What It Does:**

For UI Features:
- Expands brief description into engaging intro
- Creates "What You Can Do" section with ✅ bullet points
- Creates "How to Use It" with numbered steps
- Creates "Perfect For" with use cases
- Keeps screenshot URL

For Platform Improvements:
- Creates Before/After comparison tables
- Highlights percentage improvements
- No screenshots needed

---

### `/tech-releases`

**Purpose:** Generate Gmail-compatible HTML newsletter from markdown.

**Full Example:**

```
/tech-releases

Create a "What's New" feature highlights newsletter for RHOAI 2.36.
Source: markdown/rhoai-2.36-features.md
Output: newsletters/rhoai-2.36-features.html

Focus on:
- New user-facing features and capabilities
- UI improvements and new workflows
- Platform performance improvements with metrics
- Include visual descriptions for screenshots
- Keep it exciting and accessible (changelog style)
```

---

### Command Structure

```
/action-name

[Brief description of what you want]

Source file: release-notes/[filename.md] or markdown/[filename.md]
Template: templates/[template-name.html]  # Optional, defaults to rhoai-template.html
Output: markdown/[output.md] or newsletters/[output.html]

[Additional context or requirements]
```

---

## Template Customization

### Understanding Placeholders

The template uses these placeholders:

| Placeholder | Purpose | Example |
|-------------|---------|---------|
| `{{TITLE}}` | Browser tab title | "RHOAI 2.36 Release Notes" |
| `{{HEADER_TITLE}}` | Main H1 heading | "What's New in RHOAI 2.36" |
| `{{HEADER_SUBTITLE}}` | Intro paragraph | "Exciting new features this sprint!" |
| `{{OVERVIEW_TITLE}}` | Overview section title | "Sprint Highlights" |
| `{{OVERVIEW_DESCRIPTION}}` | Overview description | "This sprint brings..." |
| `{{OVERVIEW_HIGHLIGHTS}}` | Highlight list HTML | Multiple highlight items |
| `{{CONTENT_SECTIONS}}` | All content HTML | Feature and improvement cards |

### Creating Custom Templates

1. Copy the default template:

```bash
cp templates/rhoai-template.html templates/my-custom-template.html
```

2. Modify the structure while keeping placeholders
3. Test with sample content
4. Reference in your AI command:

```
/tech-releases

Source: markdown/content.md
Template: templates/my-custom-template.html
Output: newsletters/custom-output.html
```

### Available HTML Components

**UI Feature Card (grey background):**
- Use for features with screenshots
- Background color: #f2f2f2

**Platform Improvement Card (light green background):**
- Use for performance improvements and metrics
- Background color: #e8f5e9
- Includes metric boxes with percentages

See AGENTS.md for full HTML component templates.

---

## Previewing Newsletters

### Option 1: VS Code Live Server (Recommended)

**Install Live Server:**

1. Open VS Code Extensions (Cmd+Shift+X / Ctrl+Shift+X)
2. Search for "Live Server"
3. Install "Live Server" by Ritwick Dey
4. Restart VS Code

**Use Live Server:**

1. Open your generated HTML file
2. Right-click in the editor
3. Select "Open with Live Server"
4. Browser opens automatically with live preview
5. Changes auto-reload as you edit

### Option 2: Browser Direct Open

1. Navigate to `newsletters/` folder in Finder/Explorer
2. Drag the HTML file into your browser
3. Manually refresh (Cmd+R / Ctrl+R) after changes

---

## Image Management

### Hosting Images on Imgur

**Step-by-Step:**

1. **Go to imgur.com**
2. **Upload Image:** Click "New post" → Drag and drop your image
3. **Get Image URL:** Right-click uploaded image → "Copy image address"
4. **Use in Release Notes:**
   ```markdown
   **Screenshot:** https://i.imgur.com/ABC123.png
   ```

### Image Best Practices

**Recommended Dimensions:**
- Width: 540px (for email body)
- Aspect ratio: 16:9 (540x300px ideal)
- Format: PNG or JPG
- File size: < 300KB

**Optimization Tools:**
- **TinyPNG** - https://tinypng.com
- **Squoosh** - https://squoosh.app

---

## Troubleshooting

### Common Issues

#### Issue: Images Don't Load in Email

**Solutions:**
1. Verify images are on HTTPS (not HTTP)
2. Check imgur.com is accessible
3. Try re-uploading to imgur
4. Test image URL in incognito window

#### Issue: Newsletter Not Centered in Gmail

**Solutions:**
1. Use the template's `<center>` tags (already included)
2. Copy from browser (not source code)
3. Paste into Gmail compose (not plain text mode)

#### Issue: Formatting Lost When Copying

**Solutions:**
1. **Don't** copy from source code view
2. **Do** copy from browser rendering:
   - Open HTML in browser
   - Cmd+A (select all)
   - Cmd+C (copy)
   - Paste in Gmail compose

---

## Best Practices

### Content Creation

**Do:**
- ✅ Keep newsletters concise (3-5 sections)
- ✅ Use consistent section structure for UI features
- ✅ Include metrics for platform improvements
- ✅ Add alt text to all images
- ✅ Test links before sending

**Don't:**
- ❌ Exceed 5 main sections (too long)
- ❌ Use local file paths for images
- ❌ Mix UI feature and platform improvement styles
- ❌ Skip proofreading

### AI Prompting Tips

**Be Specific:**
```
Good: "Focus on user-facing features with screenshots"
Bad: "Make it good"
```

**Set Constraints:**
```
Good: "Keep to 3 main sections for UI features, 1 section for performance"
Bad: "However many sections you think"
```

### Testing Workflow

1. **Write** brief release notes in `release-notes/`
2. **Expand** with `/expand-release-notes`
3. **Review** the generated markdown
4. **Generate** HTML with `/tech-releases`
5. **Preview** in Live Server
6. **Check** images load
7. **Test** in browser (Cmd+A, Cmd+C)
8. **Send** test email to yourself
9. **Verify** on desktop and mobile Gmail
10. **Final send** to recipients

---

## Quick Reference

### File Paths

```
release-notes/      → Brief release notes (input)
markdown/           → Full markdown content
templates/          → HTML templates
newsletters/        → Generated HTML output
docs/               → Documentation
```

### Command Quick Reference

```
/expand-release-notes
Source: release-notes/[file.md]
Output: markdown/[file.md]

/tech-releases
Source: markdown/[file.md]
Output: newsletters/[file.html]
```

### Image Upload

1. imgur.com → "New post"
2. Upload image
3. Right-click → "Copy image address"
4. Use HTTPS URL in release notes

---

## Need Help?

- **Documentation:** [README](../README.md) | [Gmail Guide](gmail-guide.md)
- **Examples:** Check `release-notes/` and `markdown/` for samples
- **Issues:** [GitHub Issues](https://github.com/your-org/Newsletter/issues)
- **Contact:** Dashboard Platform Team

---

**Pro Tip:** Start with brief release notes, then let AI expand and generate. This two-step workflow saves time and ensures consistency!
