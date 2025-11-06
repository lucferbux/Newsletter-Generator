# Contributing to RHOAI Newsletter Generator

Thank you for your interest in contributing to the RHOAI Newsletter Generator! This document provides guidelines and instructions for contributing to the project.

---

## 🤝 How to Contribute

There are many ways to contribute to this project:

- 🐛 **Report bugs** - Help us identify and fix issues
- 💡 **Suggest features** - Share ideas for improvements
- 📝 **Improve documentation** - Help make the docs clearer
- 🎨 **Enhance templates** - Improve newsletter designs
- 🔧 **Submit code** - Fix bugs or add new features
- 📧 **Share examples** - Contribute newsletter templates

---

## 🐛 Reporting Bugs

### Before Submitting a Bug Report

1. **Check existing issues** - Your bug may already be reported
2. **Verify the bug** - Make sure it's reproducible
3. **Check documentation** - Ensure it's not a usage issue

### How to Submit a Good Bug Report

Include:

- **Clear title** - Concise description of the issue
- **Steps to reproduce** - Exact steps that trigger the bug
- **Expected behavior** - What should happen
- **Actual behavior** - What actually happens
- **Screenshots** - If applicable
- **Environment** - OS, browser, AI assistant used
- **Files** - Relevant markdown or HTML files (sanitized if needed)

**Example:**

```markdown
**Title:** Images not loading in Gmail after copy/paste

**Steps to Reproduce:**
1. Generate newsletter with `/business-achievements`
2. Open HTML in browser
3. Copy content (Cmd+A, Cmd+C)
4. Paste into Gmail compose
5. Send test email

**Expected:** Images should display inline
**Actual:** Images show as broken links

**Environment:**
- macOS 14.2
- Chrome 120
- Gmail web interface

**Images hosted on:** imgur.com (HTTPS URLs confirmed)
```

---

## 💡 Feature Requests

### Before Requesting a Feature

1. **Check existing requests** - It may already be planned
2. **Consider scope** - Is it relevant to newsletter generation?
3. **Think about use cases** - Who would benefit?

### How to Submit a Feature Request

Include:

- **Clear description** - What feature do you want?
- **Use case** - Why is this feature needed?
- **Proposed solution** - How should it work?
- **Alternatives considered** - Other approaches you've thought about
- **Examples** - Similar features in other tools

**Example:**

```markdown
**Feature:** Add a third newsletter type for "Team Updates"

**Use Case:** 
The Dashboard team wants to send monthly internal updates that blend 
technical progress with team announcements (new hires, kudos, etc.)

**Proposed Solution:**
Add `/team-updates` action that:
- Uses a more casual tone
- Includes team member highlights
- Mixes technical and non-technical content

**Alternatives:**
- Use existing `/business-achievements` and manually adjust tone
- Create a separate custom template

**Similar Features:**
- Slack's weekly digest format
- GitHub's team update emails
```

---

## 📝 Documentation Improvements

Documentation contributions are highly valued!

### Areas to Improve

- Clarify confusing instructions
- Add more examples
- Fix typos and grammar
- Improve formatting
- Add screenshots or diagrams

### Style Guidelines

- Use clear, concise language
- Write in second person ("you") for instructions
- Include code examples with syntax highlighting
- Add visual aids where helpful
- Keep consistent formatting

---

## 🎨 Template Contributions

### Template Guidelines

**Email Compatibility:**
- Use inline CSS only (no external stylesheets)
- Use web-safe fonts (Arial, Helvetica, sans-serif)
- Test in Gmail, Outlook, and Apple Mail
- Use table-based layouts for compatibility
- Avoid JavaScript
- Keep images < 300KB

**Design Principles:**
- Maintain RHOAI branding
- Ensure mobile responsiveness
- Use accessible color contrasts (WCAG AA minimum)
- Keep maximum width at 600px
- Use consistent spacing

**Template Structure:**
- Include clear placeholder comments
- Document all customization options
- Provide usage examples
- Test with sample content

---

## 🔧 Code Contributions

### Getting Started

1. **Fork the repository**

```bash
git clone https://github.com/your-username/Newsletter.git
cd Newsletter
```

2. **Create a feature branch**

```bash
git checkout -b feature/your-feature-name
```

3. **Make your changes**
   - Follow existing code style
   - Add comments for complex logic
   - Update documentation if needed

4. **Test your changes**
   - Generate test newsletters
   - Verify Gmail compatibility
   - Check cross-browser rendering

5. **Commit your changes**

```bash
git add .
git commit -m "Add feature: descriptive commit message"
```

6. **Push to your fork**

```bash
git push origin feature/your-feature-name
```

7. **Create a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your feature branch
   - Fill out the PR template

---

## 📋 Pull Request Guidelines

### Before Submitting

- [ ] Code follows existing style
- [ ] Documentation updated
- [ ] Tests pass (manual newsletter generation)
- [ ] No merge conflicts
- [ ] Commit messages are clear

### PR Description Template

```markdown
## Description
Brief description of what this PR does

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Template improvement
- [ ] Other (describe)

## Testing
How was this tested?
- [ ] Generated business newsletter
- [ ] Generated technical newsletter
- [ ] Tested in Gmail
- [ ] Tested on mobile
- [ ] Verified images load

## Screenshots
If applicable, add screenshots

## Checklist
- [ ] Documentation updated
- [ ] No lint errors
- [ ] Self-reviewed code
- [ ] Tested thoroughly

## Additional Context
Any other relevant information
```

---

## 🎯 Code Style

### HTML Templates

- Use 4-space indentation
- Include comments for sections
- Use semantic HTML where possible
- Keep inline styles organized (one property per line for readability in source)

```html
<!-- Good -->
<td style="padding:20px;
           background:#f2f2f2;
           border-radius:12px;" 
    bgcolor="#f2f2f2">
    
<!-- Not ideal -->
<td style="padding:20px;background:#f2f2f2;border-radius:12px;" bgcolor="#f2f2f2">
```

### Markdown

- Use consistent heading levels
- Include blank lines between sections
- Use code fences with language specified
- Keep line length reasonable (< 100 chars when possible)

### AI Instructions

- Use clear, imperative language
- Include examples for complex instructions
- Provide context for decisions
- Document edge cases

---

## ✅ Review Process

1. **Automated checks** - Lint and format checks run automatically
2. **Maintainer review** - A team member reviews your PR
3. **Feedback** - Requested changes or approval
4. **Merge** - Once approved, your PR is merged

**Review Timeline:**
- Most PRs reviewed within 1-3 business days
- Complex changes may take longer
- We'll communicate if delays are expected

---

## 🚀 Release Process

### Versioning

We follow semantic versioning:
- **Major (1.0.0)** - Breaking changes
- **Minor (0.1.0)** - New features, backwards compatible
- **Patch (0.0.1)** - Bug fixes

### Release Cycle

- **Patch releases** - As needed for urgent bugs
- **Minor releases** - Monthly for new features
- **Major releases** - Annually or for significant changes

---

## 📞 Getting Help

### Communication Channels

- **GitHub Discussions** - General questions and ideas
- **GitHub Issues** - Bug reports and feature requests
- **Email** - dashboard-team@redhat.com for private inquiries

### Response Times

- **Critical bugs** - Within 24 hours
- **General questions** - Within 3 business days
- **Feature requests** - Discussed in monthly planning

---

## 🏆 Recognition

Contributors are recognized in:
- `CONTRIBUTORS.md` file
- Release notes
- Project documentation

Thank you for helping make the RHOAI Newsletter Generator better! 🎉

---

## 📜 Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

By participating, you agree to uphold this code. Please report unacceptable behavior to dashboard-team@redhat.com.

---

## ❓ Questions?

Don't hesitate to reach out! We're here to help:

- Open a [GitHub Discussion](https://github.com/your-org/Newsletter/discussions)
- Email the team: dashboard-team@redhat.com
- Check the [Usage Guide](docs/usage-guide.md)

---

**Happy Contributing! 🚀**
