# RHOAI Newsletter Generator 📧

> **AI-powered HTML email newsletter generator for the Red Hat OpenShift AI (RHOAI) Dashboard team**

Transform markdown content into beautiful, Gmail-compatible HTML newsletters with AI assistance. Generate two types of newsletters: business-focused achievements for management or technical release notes for engineering teams.

---

## ✨ Features

- 🤖 **AI-Powered Content Transformation** - Automatically summarizes and adapts markdown content for your target audience
- 📧 **Gmail-Compatible HTML** - Pre-tested templates that work perfectly in Gmail and other email clients
- 🎨 **Professional Design** - Clean, responsive templates with consistent RHOAI branding
- 📝 **Markdown-Based** - Write content in simple markdown, get polished HTML newsletters
- 🔄 **Dual Newsletter Types** - Business achievements or technical releases
- 🖼️ **Image Support** - Integrated with imgur.com for reliable image hosting

---

## 🚀 Quick Start

### Prerequisites

- GitHub Copilot Chat, Claude, or similar AI assistant
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
├── .github/
│   └── copilot-instructions.md    # AI rules and actions
├── templates/
│   └── rhoai-template.html        # HTML template with placeholders
├── markdown/
│   └── (your content here)        # Source markdown files
├── newsletters/
│   └── (generated output here)    # Generated HTML newsletters
├── docs/
│   ├── usage-guide.md             # Detailed usage instructions
│   └── gmail-guide.md             # Gmail sending guide
├── README.md
└── CONTRIBUTING.md
```

---

## 📖 Usage

### Basic Workflow

1. **Create Content** - Write your newsletter content in markdown format and save it to the `markdown/` folder

2. **Generate Newsletter** - Open your AI assistant (GitHub Copilot Chat or Claude) and use one of the actions:

   **For Business Audiences:**
   ```
   /business-achievements
   
   Generate a newsletter about RHOAI 2.35 release
   Source: markdown/rhoai-2.35-release.md
   Output: newsletters/rhoai-2.35-business.html
   ```

   **For Technical Audiences:**
   ```
   /tech-releases
   
   Create technical release notes for RHOAI 3.0
   Source: markdown/rhoai-3.0-features.md
   Output: newsletters/rhoai-3.0-tech.html
   ```

3. **Preview** - Open the generated HTML file:
   - Use VS Code Live Server extension
   - Or simply open in your browser
   - Verify images load correctly

4. **Send via Gmail** - See [Gmail Guide](docs/gmail-guide.md) for detailed instructions

---

## 📚 Newsletter Types

### `/business-achievements`
**Target:** Management, executives, business units, product owners

**Focus:**
- Business impact and ROI
- Strategic advantages
- Market positioning
- Team collaboration benefits
- High-level technical achievements framed as business wins

**Tone:** Professional, strategic, results-oriented

---

### `/tech-releases`
**Target:** Engineers, developers, technical leads, DevOps teams

**Focus:**
- New feature releases
- Technical specifications
- Architecture changes
- API updates and breaking changes
- Code examples and migration guides

**Tone:** Technical, detailed, implementation-focused

---

## 🎨 Template Customization

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
- **Secondary text:** `#444746` (medium grey)

---

## 🖼️ Image Guidelines

**✅ Recommended:**
- Host on **imgur.com** (most reliable for email)
- Use HTTPS URLs only
- Keep file size < 300KB
- Recommended dimensions: 540x300px (16:9 ratio)
- Use descriptive alt text

**❌ Avoid:**
- Local file paths
- Google Drive links (unreliable in email)
- HTTP (non-secure) URLs
- Images larger than 500KB

### Uploading to Imgur

1. Go to https://imgur.com
2. Click "New post"
3. Upload your image
4. Right-click the uploaded image → "Copy image address"
5. Use that URL in your newsletter

---

## 📋 Examples

### Example 1: Business Newsletter
```
/business-achievements

Generate a newsletter highlighting modular architecture benefits.
Source: markdown/modular-arch-intro.md
Template: templates/rhoai-template.html
Output: newsletters/modular-arch-business.html

Focus on:
- 70% reduction in development effort
- Dual platform impact (Kubeflow + RHOAI)
- Faster feature delivery
```

### Example 2: Technical Release
```
/tech-releases

Create release notes for RHOAI 2.35
Source: markdown/rhoai-2.35-technical.md
Output: newsletters/rhoai-2.35-release.html

Include:
- Model Registry new features
- Model Catalog implementation details
- Breaking changes and migration steps
```

---

## 🔍 Preview Options

### VS Code / Cursor

Install **Live Server** extension:
1. Install from VS Code marketplace
2. Right-click the HTML file → "Open with Live Server"
3. Preview updates live as you edit

### Browser Preview

Simply open the HTML file in any modern browser:
- **Chrome/Edge:** Drag and drop the file
- **Firefox:** File → Open File
- **Safari:** File → Open File

---

## 📤 Sending via Gmail

**Quick Method:**
1. Open the HTML file in your browser
2. Select all (Cmd+A / Ctrl+A)
3. Copy (Cmd+C / Ctrl+C)
4. Open Gmail → Compose new message
5. Paste (Cmd+V / Ctrl+V)
6. Add recipients and send

For detailed instructions, see [Gmail Guide](docs/gmail-guide.md)

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Reporting bugs
- Suggesting features
- Submitting pull requests
- Code style and standards

---

## 📞 Support

- **Documentation:** [Usage Guide](docs/usage-guide.md) | [Gmail Guide](docs/gmail-guide.md)
- **Issues:** [GitHub Issues](https://github.com/your-org/Newsletter/issues)
- **Contact:** Dashboard Platform Team

---

## 📜 License

Copyright © 2025 Red Hat, Inc.

---

## 🔗 Related Resources

- [RHOAI Documentation](https://access.redhat.com/documentation/en-us/red_hat_openshift_ai)
- [Kubeflow Project](https://www.kubeflow.org/)
- [Gmail HTML Email Best Practices](https://developers.google.com/gmail/design/css)

---

## ⭐ Quick Tips

1. **Test emails** - Always send a test to yourself first
2. **Mobile check** - View on both desktop and mobile Gmail
3. **Image hosting** - Use imgur.com for best results
4. **Keep it concise** - Aim for 3-5 main sections per newsletter
5. **Preview first** - Use Live Server to verify formatting before sending

---

Made with ❤️ by the RHOAI Dashboard Platform Team
