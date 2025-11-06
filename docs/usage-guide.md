# Usage Guide - RHOAI Newsletter Generator

Complete guide to creating professional HTML newsletters from markdown content using AI assistance.

---

## Table of Contents

1. [Getting Started](#getting-started)
2. [Writing Markdown Content](#writing-markdown-content)
3. [Using AI Actions](#using-ai-actions)
4. [Template Customization](#template-customization)
5. [Previewing Newsletters](#previewing-newsletters)
6. [Image Management](#image-management)
7. [Troubleshooting](#troubleshooting)
8. [Best Practices](#best-practices)

---

## Getting Started

### Setup Verification

Ensure your project structure is correct:

```
Newsletter/
├── .github/copilot-instructions.md  ✓
├── templates/rhoai-template.html    ✓
├── markdown/                        ✓
├── newsletters/                     ✓
└── docs/                            ✓
```

### Choose Your AI Assistant

This project works with:
- **GitHub Copilot Chat** (VS Code / Cursor)
- **Claude** (Anthropic)
- **ChatGPT** with file access
- Any AI assistant that can read project files

---

## Writing Markdown Content

### Step 1: Create Your Markdown File

Save your content in the `markdown/` folder:

```bash
touch markdown/rhoai-2.35-release.md
```

### Step 2: Structure Your Content

Use clear headings and sections:

```markdown
# RHOAI 2.35 Release - Modular Architecture

## Overview
Brief introduction to the release and its significance.

## Key Features

### Model Registry
Description of the Model Registry feature...

### Model Catalog  
Description of the Model Catalog feature...

## Business Impact
- Reduced development time by 70%
- Dual platform support (Kubeflow + RHOAI)
- Faster feature delivery

## Screenshots
![Model Registry](https://i.imgur.com/abc123.png)
![Model Catalog](https://i.imgur.com/def456.png)

## Technical Details
- API version: v2.35
- Breaking changes: None
- Migration guide: ...

## Future Roadmap
What's coming in RHOAI 3.0...
```

### Content Guidelines

**For Business Newsletters:**
- Lead with business value
- Use metrics and outcomes
- Minimize jargon
- Focus on "why" over "how"
- Include executive-friendly language

**For Technical Newsletters:**
- Start with version/date
- Include technical specifications
- Provide code examples
- List breaking changes
- Add migration instructions

---

## Using AI Actions

### `/business-achievements`

**Full Example:**

Open your AI assistant and paste:

```
/business-achievements

Generate a business-focused newsletter for RHOAI 2.35 release.

Source file: markdown/rhoai-2.35-release.md
Template: templates/rhoai-template.html
Output: newsletters/rhoai-2.35-business.html

Focus areas:
- Highlight the 70% reduction in development effort
- Emphasize dual platform impact (Kubeflow + RHOAI)
- Frame modular architecture as competitive advantage
- Target audience: VPs, Product Managers, Business Units

Tone: Professional, strategic, results-oriented
Sections: 3-4 main topics max
```

### `/tech-releases`

**Full Example:**

```
/tech-releases

Create technical release notes for RHOAI 2.35.

Source file: markdown/rhoai-2.35-technical.md
Template: templates/rhoai-template.html
Output: newsletters/rhoai-2.35-technical.html

Include:
- Model Registry API changes
- Model Catalog implementation details
- Code examples for new features
- Breaking changes (if any)
- Migration guide from 2.34 to 2.35

Tone: Technical, detailed, actionable
Target: DevOps engineers, Platform engineers, Developers
```

### Command Structure

```
/action-name

[Brief description of what you want]

Source file: markdown/[filename.md]
Template: templates/[template-name.html]  # Optional, defaults to rhoai-template.html
Output: newsletters/[output-name.html]

[Additional context or requirements]
```

---

## Template Customization

### Understanding Placeholders

The template uses these placeholders:

| Placeholder | Purpose | Example |
|-------------|---------|---------|
| `{{TITLE}}` | Browser tab title | "RHOAI 2.35 Release Notes" |
| `{{HEADER_TITLE}}` | Main H1 heading | "Building Smarter with Modular Architecture" |
| `{{HEADER_SUBTITLE}}` | Intro paragraph | "With the latest RHOAI 2.35 release..." |
| `{{CONTENT_SECTIONS}}` | All content HTML | Multiple `<tr>` sections |

### Creating Custom Templates

1. Copy the default template:

```bash
cp templates/rhoai-template.html templates/my-custom-template.html
```

2. Modify the structure while keeping placeholders
3. Test with sample content
4. Reference in your AI command:

```
/business-achievements

Source: markdown/content.md
Template: templates/my-custom-template.html
Output: newsletters/custom-output.html
```

### Available HTML Components

The AI knows these reusable components:

**Section Header:**
```html
<tr>
    <td style="padding:20px 30px 10px 30px;">
        <h2 style="font-family:Arial, Helvetica, sans-serif;font-size:20px;margin:0;font-weight:700;color:#2c3e50;text-align:center;">
            Section Title
        </h2>
        <p style="font-family:Arial, Helvetica, sans-serif;margin:10px 0 0 0;font-size:15px;line-height:22px;color:#444746;text-align:center;">
            Section description
        </p>
    </td>
</tr>
```

**Content Card:**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;margin-bottom:15px;">
            <tr>
                <td style="padding:20px;background:#f2f2f2;border-radius:12px;" bgcolor="#f2f2f2">
                    <span style="font-size:32px;margin-bottom:10px;display:block;">🎯</span>
                    <h3 style="font-family:Arial, Helvetica, sans-serif;font-size:16px;margin:0 0 10px 0;font-weight:700;color:#2c3e50;">
                        Card Title
                    </h3>
                    <p style="font-family:Arial, Helvetica, sans-serif;margin:0;font-size:14px;line-height:20px;color:#3c4043;">
                        Card content goes here...
                    </p>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

**Image with Caption:**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;margin-bottom:20px;">
            <tr>
                <td style="padding:15px;background:#f2f2f2;border-radius:12px;" bgcolor="#f2f2f2">
                    <p style="font-family:Arial, Helvetica, sans-serif;font-size:16px;font-weight:700;color:#2c3e50;margin:0 0 10px 0;text-align:center;">
                        Image Title
                    </p>
                    <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;">
                        <tr>
                            <td align="center" style="padding:10px;">
                                <img src="https://i.imgur.com/IMAGE_ID.png" 
                                     alt="Descriptive alt text" 
                                     width="540" 
                                     style="display:block;width:100%;max-width:540px;height:auto;border:2px solid #dfe1e5;border-radius:8px;" />
                            </td>
                        </tr>
                    </table>
                    <p style="font-family:Arial, Helvetica, sans-serif;margin:10px 0 0 0;font-size:13px;line-height:18px;color:#3c4043;text-align:center;">
                        Image caption or description
                    </p>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

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

**Benefits:**
- ✅ Live reload on changes
- ✅ No manual refresh needed
- ✅ Works with all browsers

### Option 2: Cursor Live Preview

**If using Cursor editor:**

1. Open your HTML file
2. Click the preview icon (top-right)
3. Or use Cmd+K V (Mac) / Ctrl+K V (Windows)

### Option 3: Browser Direct Open

**Simple but manual:**

1. Navigate to `newsletters/` folder in Finder/Explorer
2. Drag the HTML file into your browser
3. Manually refresh (Cmd+R / Ctrl+R) after changes

**Supported Browsers:**
- Chrome (recommended)
- Firefox
- Safari
- Edge

---

## Image Management

### Hosting Images on Imgur

**Step-by-Step:**

1. **Go to imgur.com**
   - No account required for uploads
   - Account recommended for managing images

2. **Upload Image:**
   - Click "New post" (top left)
   - Drag and drop your image
   - Or click to browse files

3. **Get Image URL:**
   - Right-click the uploaded image
   - Select "Copy image address" (Chrome) or "Copy Image Link" (Firefox)
   - URL format: `https://i.imgur.com/ABC123.png`

4. **Use in Markdown:**
   ```markdown
   ![Alt text](https://i.imgur.com/ABC123.png)
   ```

### Image Best Practices

**Recommended Dimensions:**
- Width: 540px (for email body)
- Aspect ratio: 16:9 (540x300px ideal)
- Format: PNG or JPG
- File size: < 300KB

**Optimization Tools:**
- **TinyPNG** - https://tinypng.com (compress without quality loss)
- **Squoosh** - https://squoosh.app (Google's optimizer)
- **ImageOptim** - Mac app for bulk optimization

**Taking Screenshots:**

For best results:
1. Set browser window to 1080px width
2. Use macOS: Cmd+Shift+4, select area
3. Use Windows: Snipping Tool or Win+Shift+S
4. Crop to relevant content
5. Compress before uploading

### Alternative Image Hosts

**GitHub (for project images):**

```
https://raw.githubusercontent.com/username/repo/main/images/screenshot.png
```

**Pros:** Free, permanent, version controlled
**Cons:** Requires GitHub repo setup

**Cloudinary (professional option):**

Free tier: 25GB bandwidth/month
**Pros:** CDN, automatic optimization
**Cons:** Requires account setup

---

## Troubleshooting

### Common Issues

#### Issue: Images Don't Load in Email

**Symptoms:** Images show as broken links in Gmail

**Solutions:**
1. Verify images are on HTTPS (not HTTP)
2. Check imgur.com is accessible
3. Try re-uploading to imgur
4. Clear browser cache
5. Test image URL in incognito window

**Debug Steps:**
```bash
# Test image URL
curl -I https://i.imgur.com/YOUR_IMAGE_ID.png

# Should return: HTTP/2 200
```

#### Issue: Newsletter Not Centered in Gmail

**Symptoms:** Content appears left-aligned after pasting

**Solutions:**
1. Use the template's `<center>` tags (already included)
2. Copy from browser (not source code)
3. Paste into Gmail compose (not plain text mode)
4. Send test to yourself first

#### Issue: Formatting Lost When Copying

**Symptoms:** Styles don't transfer to Gmail

**Solutions:**
1. **Don't** copy from source code view
2. **Do** copy from browser rendering:
   - Open HTML in browser
   - Cmd+A (select all)
   - Cmd+C (copy)
   - Paste in Gmail compose

#### Issue: AI Generates Incorrect Format

**Symptoms:** Output doesn't match expectations

**Solutions:**
1. Be more specific in your prompt
2. Reference the template explicitly
3. Provide example of desired output
4. Check markdown formatting
5. Verify AI has access to `.github/copilot-instructions.md`

---

## Best Practices

### Content Creation

**Do:**
- ✅ Keep newsletters concise (3-5 sections)
- ✅ Use bullet points for lists
- ✅ Include clear headings
- ✅ Add alt text to all images
- ✅ Test links before sending

**Don't:**
- ❌ Exceed 5 main sections (too long)
- ❌ Use local file paths for images
- ❌ Include JavaScript or external CSS
- ❌ Forget to test mobile rendering
- ❌ Skip proofreading

### AI Prompting Tips

**Be Specific:**
```
Good: "Focus on business ROI and strategic advantages"
Bad: "Make it good"
```

**Provide Context:**
```
Good: "Target audience: VPs and Product Managers who may not know technical details"
Bad: "For management"
```

**Set Constraints:**
```
Good: "Keep to 3 main sections, each with 2-3 cards"
Bad: "However many sections you think"
```

### Testing Workflow

1. **Generate** newsletter with AI
2. **Preview** in Live Server
3. **Check** images load
4. **Review** content accuracy
5. **Test** in browser (Cmd+A, Cmd+C)
6. **Send** test email to yourself
7. **Verify** on desktop Gmail
8. **Verify** on mobile Gmail
9. **Final send** to recipients

### Version Control

**Track Your Newsletters:**

```bash
git add newsletters/rhoai-2.35-business.html
git commit -m "Add: RHOAI 2.35 business newsletter"
git push
```

**Benefits:**
- History of all newsletters
- Easy to reference past content
- Collaborative editing
- Rollback if needed

---

## Advanced Usage

### Batch Generation

Generate multiple newsletters at once:

```
/business-achievements

Generate 2 newsletters from the same markdown:

1. Executive summary (output: newsletters/rhoai-2.35-exec.html)
   - Ultra-concise, 2 sections only
   - Focus: ROI and strategic wins
   
2. Detailed business (output: newsletters/rhoai-2.35-business-full.html)
   - Comprehensive, 4-5 sections
   - Include metrics and case studies

Source: markdown/rhoai-2.35-release.md
```

### Custom Styling

Override template colors in your prompt:

```
/tech-releases

Use custom color scheme:
- Headers: #0066cc (bright blue)
- Cards: #e6f2ff (light blue)
- Accent: #004080 (dark blue)

Source: markdown/special-announcement.md
Output: newsletters/special-blue.html
```

### A/B Testing

Create variations to test:

```
/business-achievements

Create 2 versions with different approaches:

Version A (newsletters/rhoai-metric-focus.html):
- Lead with 70% efficiency improvement
- Use numbers and metrics throughout
- Data-driven narrative

Version B (newsletters/rhoai-story-focus.html):
- Lead with customer success story
- Narrative and storytelling approach
- Metrics as supporting evidence

Source: markdown/rhoai-2.35-release.md
```

---

## Quick Reference

### Command Template

```
/[action]

[Description]

Source file: markdown/[file.md]
Template: templates/[template.html]  # optional
Output: newsletters/[output.html]

[Additional instructions]
```

### File Paths

```
markdown/           → Your content (input)
templates/          → HTML templates
newsletters/        → Generated output
docs/               → Documentation
.github/            → AI instructions
```

### Preview Shortcuts

- **VS Code Live Server:** Right-click → "Open with Live Server"
- **Cursor Preview:** Cmd+K V (Mac) / Ctrl+K V (Windows)
- **Browser:** Drag HTML file to browser window

### Image Upload

1. imgur.com → "New post"
2. Upload image
3. Right-click → "Copy image address"
4. Use HTTPS URL in markdown

---

## Need Help?

- **Documentation:** [README](../README.md) | [Gmail Guide](gmail-guide.md)
- **Examples:** Check `newsletters/` for samples
- **Issues:** [GitHub Issues](https://github.com/your-org/Newsletter/issues)
- **Contact:** Dashboard Platform Team

---

**Pro Tip:** Bookmark this guide and keep it open while generating newsletters! 📚
