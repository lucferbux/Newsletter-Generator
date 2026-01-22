# RHOAI Newsletter Generator

> **AI-powered HTML email newsletter generator for the Red Hat OpenShift AI (RHOAI) Dashboard team**

Transform release notes into beautiful, Gmail-compatible HTML newsletters with AI assistance. Uses a two-step workflow to expand brief release notes into polished newsletters.

---

## Features

- **Two-Step Workflow** - Write brief release notes, AI expands and generates HTML
- **Gmail-Compatible HTML** - Pre-tested templates that work perfectly in Gmail
- **Two Content Types** - UI Features (with screenshots) and Platform Improvements (metrics-based)
- **Professional Design** - Clean, responsive templates with consistent RHOAI branding
- **Markdown-Based** - Write content in simple markdown, get polished HTML newsletters

---

## Quick Start

### Prerequisites

- Claude Code, GitHub Copilot Chat, or similar AI assistant
- Modern web browser
- Gmail account (for sending)
- VS Code or Cursor editor (recommended for Live Server preview)

### Installation

1. Clone this repository:
```bash
git clone https://github.com/your-org/Newsletter.git
cd Newsletter
```

2. Verify the folder structure:
```
Newsletter/
├── AGENTS.md                    # AI agent instructions
├── CLAUDE.md                    # Claude Code instructions
├── templates/
│   └── rhoai-template.html      # HTML template with placeholders
├── release-notes/
│   └── example-release-notes.md # Brief release notes (input)
├── markdown/
│   └── example-feature-newsletter.md # Full markdown (source)
├── newsletters/
│   └── (generated output here)  # Generated HTML newsletters
├── docs/
│   ├── usage-guide.md           # Detailed usage instructions
│   └── gmail-guide.md           # Gmail sending guide
├── README.md
└── CONTRIBUTING.md
```

---

## Usage

### Workflow Overview

The newsletter generation follows a two-step workflow:

```
release-notes/*.md → /expand-release-notes → markdown/*.md → /tech-releases → newsletters/*.html
```

### Step 1: Write Brief Release Notes

Create concise release notes in `release-notes/` folder:

```markdown
# RHOAI 2.36 Sprint Release Notes

**Sprint:** December 2025
**Version:** 2.36.0

## UI Features

### Model Comparison View
Compare multiple models side-by-side.

**Screenshot:** https://i.imgur.com/EXAMPLE.png

- Compare up to 4 models
- Export as PDF

## Platform Improvements

### API Optimization
- Dashboard load: 2.1s → 0.8s (62% faster)
```

### Step 2: Expand to Full Markdown

Use AI to expand brief notes into full newsletter content:

```
/expand-release-notes

Source: release-notes/rhoai-2.36-sprint.md
Output: markdown/rhoai-2.36-features.md
```

### Step 3: Generate HTML Newsletter

Generate Gmail-compatible HTML:

```
/tech-releases

Source: markdown/rhoai-2.36-features.md
Output: newsletters/rhoai-2.36-features.html
```

### Step 4: Preview and Send

1. Open the HTML file in your browser
2. Select all (Cmd+A / Ctrl+A)
3. Copy (Cmd+C / Ctrl+C)
4. Paste in Gmail compose
5. Send!

---

## Content Types

### UI Features (with screenshots)

For features with visible UI changes:
- Include screenshot URL (imgur.com)
- "What You Can Do" section with checkmarks
- "How to Use It" with numbered steps
- "Perfect For" with use cases

### Platform Improvements (metrics-based)

For backend improvements and performance gains:
- No screenshot required
- Before/After metrics tables
- Percentage improvements
- Light green background in HTML (#e8f5e9)

---

## Available Commands

### `/expand-release-notes`
**Purpose:** Transform brief release notes into full newsletter-ready markdown

**Input:** Brief release notes from `release-notes/` folder
**Output:** Full markdown file in `markdown/` folder

---

### `/tech-releases`
**Purpose:** Generate Gmail-compatible HTML newsletter

**Input:** Full markdown from `markdown/` folder
**Output:** HTML newsletter in `newsletters/` folder

---

## Template Customization

The default template (`templates/rhoai-template.html`) uses these placeholders:

- `{{TITLE}}` - Browser tab title
- `{{HEADER_TITLE}}` - Main newsletter heading (H1)
- `{{HEADER_SUBTITLE}}` - Supporting paragraph under heading
- `{{CONTENT_SECTIONS}}` - All content sections (dynamically generated)

### Color Scheme

- **Background:** `#f2f2f2` (light grey)
- **Content background:** `#ffffff` (white)
- **Primary text:** `#1f1f1f` (dark grey)
- **Headings:** `#2c3e50` (elegant dark grey-blue)
- **Platform improvements:** `#e8f5e9` (light green)

---

## Image Guidelines

**Recommended:**
- Host on **imgur.com** (most reliable for email)
- Use HTTPS URLs only
- Keep file size < 300KB
- Recommended dimensions: 540x300px (16:9 ratio)

**Avoid:**
- Local file paths
- Google Drive links (unreliable in email)
- HTTP (non-secure) URLs

---

## Examples

### Brief Release Notes → Full Newsletter

**Input (release-notes/example.md):**
```markdown
### Model Comparison
Compare models side-by-side.

**Screenshot:** https://i.imgur.com/ABC123.png

- Compare 4 models
- Export PDF
```

**Output (markdown/example.md):**
```markdown
## Model Comparison View

**Compare models side-by-side to make better decisions**

### What You Can Do

- Compare Multiple Models - View up to 4 models side-by-side
- Export Results - Download comparisons as PDF

### How to Use It

1. Open Model Catalog
2. Select models to compare
3. Click "Compare"

### Perfect For

- Choosing models for production
- Evaluating upgrades

![Model comparison](https://i.imgur.com/ABC123.png)
```

---

## Preview Options

### VS Code / Cursor

Install **Live Server** extension:
1. Install from VS Code marketplace
2. Right-click the HTML file → "Open with Live Server"
3. Preview updates live as you edit

### Browser Preview

Simply open the HTML file in any modern browser.

---

## Sending via Gmail

**Quick Method:**
1. Open the HTML file in your browser
2. Select all (Cmd+A / Ctrl+A)
3. Copy (Cmd+C / Ctrl+C)
4. Open Gmail → Compose new message
5. Paste (Cmd+V / Ctrl+V)
6. Add recipients and send

For detailed instructions, see [Gmail Guide](docs/gmail-guide.md)

---

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Support

- **Documentation:** [Usage Guide](docs/usage-guide.md) | [Gmail Guide](docs/gmail-guide.md)
- **Issues:** [GitHub Issues](https://github.com/your-org/Newsletter/issues)
- **Contact:** Dashboard Platform Team

---

## License

Copyright 2025 Red Hat, Inc.

---

## Quick Tips

1. **Start with brief notes** - Let AI do the expansion
2. **Use two content types** - UI features with screenshots, platform improvements with metrics
3. **Test emails** - Always send a test to yourself first
4. **Image hosting** - Use imgur.com for best results
5. **Preview first** - Use Live Server to verify formatting before sending

---

Made with love by the RHOAI Dashboard Platform Team
