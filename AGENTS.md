# RHOAI Newsletter Generator - AI Agent Instructions

This project generates HTML email newsletters from markdown content for the Red Hat OpenShift AI (RHOAI) Dashboard team.

## CRITICAL: Gmail Compatibility Requirements

**ALL generated HTML must be Gmail-compatible. This means:**

### Allowed in Gmail:
- Inline CSS only (style="..." attributes)
- Table-based layouts (no flexbox, no CSS grid)
- Web-safe fonts: Arial, Helvetica, sans-serif, Georgia, Times New Roman, Courier
- Basic HTML tags: `<table>`, `<tr>`, `<td>`, `<p>`, `<h1-h6>`, `<a>`, `<img>`, `<span>`, `<center>`
- HTTPS image URLs (publicly accessible - imgur.com recommended)
- Background colors via inline styles AND bgcolor attribute
- Simple CSS properties: color, font-size, padding, margin, background, border, text-align, line-height

### Forbidden in Gmail:
- External CSS files (`<link rel="stylesheet">`)
- `<style>` tags in `<head>`
- JavaScript (any `<script>` tags)
- Forms (`<form>`, `<input>`, `<button>`)
- Video/audio tags (`<video>`, `<audio>`)
- CSS animations or transitions
- Flexbox or CSS Grid
- Position: absolute/fixed
- CSS pseudo-elements (::before, ::after)
- Custom fonts (@font-face)
- SVG inline code (use PNG/JPG images instead)
- Local file paths for images

### Gmail Best Practices:
1. **Maximum width: 600px** - Wider emails may be cut off
2. **Use `<center>` tags** - Gmail sometimes strips CSS centering
3. **Double-specify colors** - Use both `bgcolor="..."` and `style="background:..."`
4. **Test in Gmail** - Always test before sending
5. **Mobile-first** - Use `width:100%` and `max-width` for responsive images
6. **Avoid nested tables >3 levels deep** - Gmail rendering issues
7. **All images must be HTTPS** - HTTP images will be blocked

---

## Workflow Overview

The newsletter generation follows a two-step workflow:

```
release-notes/*.md → /expand-release-notes → markdown/*.md → /tech-releases → newsletters/*.html
```

### Step 1: Create Brief Release Notes
Write concise release notes in `release-notes/` folder with key features and metrics.

### Step 2: Expand to Full Markdown
Use `/expand-release-notes` to transform brief notes into full newsletter content.

### Step 3: Generate HTML Newsletter
Use `/tech-releases` to generate the final Gmail-compatible HTML.

---

## Content Types

### UI Features (with screenshots)
Features that have visible UI changes should include:
- Screenshot URL (imgur.com recommended)
- "What You Can Do" section with ✅ checkmarks
- "How to Use It" with numbered steps
- "Perfect For" with use cases

### Platform Improvements (metrics-based)
Backend improvements, performance gains, and technical enhancements:
- No screenshot required
- Before/After metrics tables
- Percentage improvements
- Developer experience benefits

---

## Available Actions

### `/expand-release-notes`
**Purpose:** Transform brief release notes into full newsletter-ready markdown content.

**Input:** Brief release notes from `release-notes/` folder
**Output:** Full markdown file in `markdown/` folder

**Transformation Rules:**

1. **For UI Features:**
   - Expand brief description into engaging intro paragraph
   - Create "What You Can Do" section with ✅ bullet points
   - Create "How to Use It" section with numbered steps
   - Create "Perfect For" section with use cases
   - Keep screenshot URL as-is

2. **For Platform Improvements:**
   - Keep metrics-focused format
   - Create Before/After comparison tables
   - Highlight percentage improvements prominently
   - No screenshots needed

**Example Input (brief):**
```markdown
### Model Comparison View
Compare multiple models side-by-side with unified metrics display.

**Screenshot:** https://i.imgur.com/ABC123.png

- Compare up to 4 models simultaneously
- See performance metrics in unified view
- Export comparison results as PDF
```

**Example Output (expanded):**
```markdown
## 🔍 Model Comparison View

**Compare models side-by-side to make better decisions**

No more switching between tabs! The new comparison view lets you evaluate up to 4 models at once with unified metrics.

### What You Can Do

✅ **Compare Multiple Models** - View up to 4 models side-by-side

✅ **Unified Metrics** - See latency, throughput, and accuracy in one view

✅ **Export Results** - Download comparisons as PDF or JSON

### How to Use It

1. **Open Model Catalog** → Browse available models
2. **Select Models** → Check the boxes on models you want to compare
3. **Click "Compare"** → Opens the comparison view
4. **Export or Save** → Keep your findings

### Perfect For

- Choosing between similar models for production
- Evaluating model upgrades before deployment
- Team discussions about model tradeoffs

![Model comparison view](https://i.imgur.com/ABC123.png)
```

---

### `/tech-releases`
**Purpose:** Generate a newsletter highlighting new features, improvements, and what's changed in the product release.

**Target Audience:** Product users, engineers, developers, technical leads, DevOps teams

**Content Focus:**
- New features and capabilities (what users can do now)
- User-facing improvements and enhancements
- UI/UX changes and new workflows
- Performance improvements (user impact)
- Key highlights with screenshots/visuals
- Getting started with new features
- Practical examples and use cases

**Tone:** Informative, enthusiastic, user-focused (not deeply technical)

**Example Structure:**
- "What's New" overview
- Feature highlights with descriptions
- Screenshots or visual examples
- How users benefit from changes
- Quick start or "try it now" sections
- No deep code examples or architecture details

---

## Newsletter Generation Workflow

When a user requests newsletter generation, follow these steps:

### Step 1: Read and Analyze Markdown
1. Read the markdown file from the `markdown/` folder
2. Identify the key themes, topics, and content structure
3. Extract any image URLs (must be from imgur.com or similar public hosting)
4. **Image Warning:** If images are found, verify they are publicly hosted (imgur.com recommended). Local or restricted URLs will not work in emails.

### Step 2: Transform Content
- Focus on what's new and what users can do
- Highlight user-facing features and improvements
- Use clear, accessible language (avoid deep technical jargon)
- Include screenshots or visual descriptions
- Organize by feature area
- Show practical use cases and benefits
- Keep it exciting and engaging (changelog style)
- Link to documentation for "learn more"
- No code snippets unless absolutely necessary for clarity

### Step 3: Generate Gmail-Compatible HTML Newsletter

**CRITICAL: Every HTML element must follow Gmail compatibility rules!**

1. Use the template from `templates/rhoai-template.html` (or user-specified template)
2. Replace placeholders:
   - `{{TITLE}}` - Page title for browser tab
   - `{{HEADER_TITLE}}` - Main newsletter heading (H1)
   - `{{HEADER_SUBTITLE}}` - Supporting paragraph under heading
   - `{{OVERVIEW_TITLE}}` - Overview section title
   - `{{OVERVIEW_DESCRIPTION}}` - Overview description
   - `{{OVERVIEW_HIGHLIGHTS}}` - List of highlights
   - `{{CONTENT_SECTIONS}}` - All content sections in HTML

3. **Gmail-Compatible Content Section Components:**

**Section with Title & Description:**
```html
<tr>
    <td style="padding:20px 30px 10px 30px;">
        <h2 style="font-family:Arial, Helvetica, sans-serif;font-size:20px;margin:0;font-weight:700;color:#2c3e50;text-align:center;">Section Title</h2>
        <p style="font-family:Arial, Helvetica, sans-serif;margin:10px 0 0 0;font-size:15px;line-height:22px;color:#444746;text-align:center;">Section description text</p>
    </td>
</tr>
```

**UI Feature Card (with bgcolor attribute for Gmail):**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;margin-bottom:15px;">
            <tr>
                <td style="padding:20px;background:#f2f2f2;border-radius:12px;" bgcolor="#f2f2f2">
                    <span style="font-size:32px;margin-bottom:10px;display:block;">🎯</span>
                    <h3 style="font-family:Arial, Helvetica, sans-serif;font-size:16px;margin:0 0 10px 0;font-weight:700;color:#2c3e50;">Card Title</h3>
                    <p style="font-family:Arial, Helvetica, sans-serif;margin:0;font-size:14px;line-height:20px;color:#3c4043;">Card content paragraph text goes here.</p>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

**Platform Improvement Card (light green, metrics-based, no image):**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;margin-bottom:15px;">
            <tr>
                <td style="padding:20px;background:#e8f5e9;border-radius:12px;" bgcolor="#e8f5e9">
                    <span style="font-size:32px;margin-bottom:10px;display:block;">⚡</span>
                    <h3 style="font-family:Arial, Helvetica, sans-serif;font-size:16px;margin:0 0 10px 0;font-weight:700;color:#2c3e50;">Performance Improvement Title</h3>
                    <p style="font-family:Arial, Helvetica, sans-serif;margin:0 0 15px 0;font-size:14px;line-height:20px;color:#3c4043;">Description of the improvement.</p>
                    <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;">
                        <tr>
                            <td style="padding:10px;background:#ffffff;border-radius:8px;text-align:center;width:33%;" bgcolor="#ffffff">
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:24px;font-weight:700;color:#2e7d32;display:block;">62%</span>
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:12px;color:#666;">Faster Load</span>
                            </td>
                            <td style="width:10px;"></td>
                            <td style="padding:10px;background:#ffffff;border-radius:8px;text-align:center;width:33%;" bgcolor="#ffffff">
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:24px;font-weight:700;color:#2e7d32;display:block;">54%</span>
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:12px;color:#666;">Less Memory</span>
                            </td>
                            <td style="width:10px;"></td>
                            <td style="padding:10px;background:#ffffff;border-radius:8px;text-align:center;width:33%;" bgcolor="#ffffff">
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:24px;font-weight:700;color:#2e7d32;display:block;">3x</span>
                                <span style="font-family:Arial, Helvetica, sans-serif;font-size:12px;color:#666;">Dev Speed</span>
                            </td>
                        </tr>
                    </table>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

**Image Section (MUST use HTTPS URLs):**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;margin-bottom:20px;">
            <tr>
                <td style="padding:15px;background:#f2f2f2;border-radius:12px;" bgcolor="#f2f2f2">
                    <p style="font-family:Arial, Helvetica, sans-serif;font-size:16px;font-weight:700;color:#2c3e50;margin:0 0 10px 0;text-align:center;">Image Caption</p>
                    <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;">
                        <tr>
                            <td align="center" style="padding:10px;">
                                <img src="https://i.imgur.com/EXAMPLE.png"
                                     alt="Descriptive alt text"
                                     width="540"
                                     style="display:block;width:100%;max-width:540px;height:auto;border:2px solid #dfe1e5;border-radius:8px;" />
                            </td>
                        </tr>
                    </table>
                    <p style="font-family:Arial, Helvetica, sans-serif;margin:10px 0 0 0;font-size:13px;line-height:18px;color:#3c4043;text-align:center;">Image description or context</p>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

**List Items (use table rows, not `<ul>`/`<li>`):**
```html
<tr>
    <td style="padding:10px 30px;">
        <table role="presentation" style="width:100%;border-collapse:collapse;border:0;border-spacing:0;">
            <tr>
                <td style="padding:5px 0;">
                    <span style="font-family:Arial, Helvetica, sans-serif;font-size:14px;color:#3c4043;">✓ First item</span>
                </td>
            </tr>
            <tr>
                <td style="padding:5px 0;">
                    <span style="font-family:Arial, Helvetica, sans-serif;font-size:14px;color:#3c4043;">✓ Second item</span>
                </td>
            </tr>
        </table>
    </td>
</tr>
```

**Links (always use full HTTPS URLs):**
```html
<a href="https://example.com/full-path" style="color:#1a73e8;text-decoration:underline;font-family:Arial, Helvetica, sans-serif;">Link Text</a>
```

4. **Gmail Validation Checklist Before Saving:**
   - [ ] All styles are inline (no `<style>` tags)
   - [ ] Only table-based layout (no flexbox/grid)
   - [ ] All fonts are web-safe (Arial, Helvetica, sans-serif)
   - [ ] Background colors have both `style="background:..."` AND `bgcolor="..."`
   - [ ] All image URLs are HTTPS (https://i.imgur.com/...)
   - [ ] No JavaScript anywhere
   - [ ] No forms or buttons
   - [ ] Maximum width 600px
   - [ ] All links have full HTTPS URLs
   - [ ] No SVG inline code
   - [ ] No external CSS files

5. Save the generated HTML to the `newsletters/` folder (or user-specified output folder)

### Step 4: Provide Output Summary

After generation, provide:
1. Confirmation of file creation with path
2. Brief content summary
3. Image URL check results (if any)
4. Gmail compatibility confirmation
5. Next steps: How to preview and send via Gmail

---

## Example User Prompts

**Expand Release Notes:**
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

**Feature Highlights Newsletter:**
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

## Template Selection

### Default Template
Use `templates/rhoai-template.html` for standard newsletters.

### Custom Templates
Create custom templates by copying and modifying the default:
```bash
cp templates/rhoai-template.html templates/my-template.html
```

Reference in prompts:
```
Template: templates/my-template.html
```

---

## Best Practices

### Content
- Keep newsletters concise (3-5 main sections max)
- Use bullet points for lists
- Highlight key takeaways
- Include clear calls-to-action when relevant

### UI Features
- Always include screenshot URLs (imgur.com)
- Use consistent section structure:
  - What You Can Do (✅ checkmarks)
  - How to Use It (numbered steps)
  - Perfect For (use cases)
- Add emoji to section headers

### Platform Improvements
- Focus on metrics and percentages
- Use Before/After comparison tables
- Light green background (#e8f5e9) to distinguish from UI features
- No screenshots required

### Images
- **Always use publicly hosted images** (imgur.com recommended)
- Optimize images to < 300KB each
- Use descriptive alt text
- Maintain 16:9 aspect ratio where possible
- Recommended size: 540px width
- **MUST be HTTPS URLs**

### Gmail-Compatible Design
- **Stick to the template's color scheme:**
  - Background: #f2f2f2 (grey)
  - White content: #ffffff
  - Primary text: #1f1f1f
  - Secondary text: #444746
  - Accent: #2c3e50 (dark grey-blue)
  - Platform improvements: #e8f5e9 (light green)
- **Use emojis sparingly** (1 per card/section max)
- **Maintain consistent spacing** between sections
- **Double-specify backgrounds:** Both `bgcolor="..."` and `style="background:..."`
- **Test centering:** Use both `<center>` tags and `text-align:center`

### Gmail Rendering Rules
- **No external CSS files** - Everything must be inline
- **All styles must be inline** - Within `style="..."` attributes
- **No JavaScript** - Gmail strips all scripts
- **No `<button>` elements** - Use `<a>` tags styled as buttons
- **Use web-safe fonts** - Arial, Helvetica, sans-serif only
- **Images must be HTTPS URLs** - No local paths
- **Table-based layout only** - No flexbox or grid
- **Maximum width 600px** - Wider content may be cut off
- **Test in Gmail** - Always verify rendering before sending

---

## Validation Checklist

Before finalizing a newsletter, verify:
- [ ] All placeholders replaced
- [ ] Images are publicly accessible HTTPS URLs
- [ ] No broken HTML tags
- [ ] Consistent formatting and spacing
- [ ] Content follows UI Feature or Platform Improvement structure
- [ ] File saved to correct output path
- [ ] Footer includes "Dashboard Platform Team"
- [ ] **ALL styles are inline (no `<style>` tags)**
- [ ] **Only table-based layout used**
- [ ] **All fonts are web-safe (Arial, Helvetica, sans-serif)**
- [ ] **No JavaScript present**
- [ ] **No forms or buttons**
- [ ] **All images are HTTPS**
- [ ] **Maximum width 600px**

---

## Error Handling

**If markdown file not found:**
- List available markdown files in `markdown/` folder
- Ask user to verify file name

**If release notes file not found:**
- List available files in `release-notes/` folder
- Ask user to verify file name

**If image URLs are invalid:**
- Warn the user that local/private images won't work in Gmail
- Suggest using imgur.com with HTTPS
- Provide placeholder text in the HTML

**If template not found:**
- Fall back to `templates/rhoai-template.html`
- Notify user of the fallback

**If non-Gmail-compatible HTML detected:**
- Flag the issue immediately
- Explain what needs to be fixed
- Provide Gmail-compatible alternative

---

## Post-Generation Instructions

After generating the newsletter, remind the user:

1. **Preview the newsletter:**
   - Open the HTML file in a browser
   - Use VS Code Live Server or editor's preview feature
   - Check that all images load correctly
   - Verify layout is centered and width is 600px

2. **Send via Gmail:**
   - See `docs/gmail-guide.md` for detailed instructions
   - Quick method: Open HTML in browser → Cmd+A → Cmd+C → Paste in Gmail compose
   - **Important:** Copy from browser preview, NOT from source code

3. **Test before sending:**
   - Send to yourself first
   - Check on desktop Gmail web interface
   - Check on mobile Gmail app
   - Verify images load in email client
   - Verify layout is centered
   - Test all links

4. **Gmail Compatibility Check:**
   - Open in Gmail and verify no layout breaks
   - Check that colors and fonts display correctly
   - Ensure images are not blocked (HTTPS only)
   - Confirm mobile responsiveness

---

## Support

**For questions or issues:**
- Check `docs/usage-guide.md` for detailed instructions
- Review `CONTRIBUTING.md` for contribution guidelines
- Contact: Dashboard Platform Team
