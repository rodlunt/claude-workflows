# Claude Workflows - Project Starter Reference

A reference folder for starting new projects with Claude Code. Contains workflows, templates, and best practices.

## Quick Start

When starting a new project:

1. **Copy the CLAUDE.md template** to your project root:
   ```bash
   cp templates/CLAUDE.md /path/to/your/project/CLAUDE.md
   ```

2. **Copy GitHub Actions** (optional) for automated reviews:
   ```bash
   cp -r templates/.github /path/to/your/project/
   ```

3. **Customize** the CLAUDE.md with your project's specifics

---

## Folder Structure

```
claude-workflows/
├── templates/              # Ready-to-use templates
│   ├── CLAUDE.md           # Project config template for Claude
│   └── .github/workflows/  # GitHub Actions for automated reviews
│       ├── code-review.yml
│       └── security-review.yml
│
├── code-review/            # Code review reference docs
│   ├── pragmatic-code-review-slash-command.md
│   └── pragmatic-code-review-subagent.md
│
├── security-review/        # Security review reference docs
│   └── security-review-slash-command.md
│
└── design-review/          # Design review reference docs
    ├── design-review-agent.md
    ├── design-principles-example.md
    └── design-review-slash-command.md
```

---

## What's Included

### Templates (`/templates`)

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project configuration file that Claude reads automatically. Defines tech stack, conventions, commands, and review guidelines. |
| `.github/workflows/code-review.yml` | GitHub Action for automated code review on PRs |
| `.github/workflows/security-review.yml` | GitHub Action for automated security scanning on PRs |

### Code Review (`/code-review`)

"Pragmatic Quality" framework - balances engineering standards with development speed.

- **Slash command:** Run `/review` for on-demand code analysis
- **Subagent:** Detailed review with 7 priority levels (architecture → documentation)
- **Triage:** Critical/Blocker → Improvement → Nit

### Security Review (`/security-review`)

OWASP-based vulnerability scanning with high-confidence filtering (>80%).

- **Checks:** SQL injection, XSS, auth issues, secrets exposure, RCE
- **Output:** Severity-classified findings with fix recommendations
- **Goal:** Minimize false positives

### Design Review (`/design-review`)

Live UI testing using Playwright with industry best practices.

- **7-phase review:** Interaction → Responsiveness → Visual Polish → Accessibility → Robustness → Code Health
- **Standards:** Inspired by Stripe, Airbnb, Linear
- **Accessibility:** WCAG 2.1 AA compliance

---

## GitHub Secrets Required

To use the GitHub Actions, add these secrets to your repository:

| Secret | Description |
|--------|-------------|
| `CLAUDE_CODE_OAUTH_TOKEN` | OAuth token for Claude Code Action |
| `ANTHROPIC_API_KEY` | API key for security review action |

---

## Usage Tips

### CLAUDE.md Best Practices

1. Keep it concise - Claude reads this every session
2. Include your actual commands (dev, build, test, lint)
3. Document architectural decisions
4. List environment variables
5. Add project-specific conventions

### Running Reviews Manually

```bash
# Code review (in your project directory)
claude "/review"

# Security review
claude "/security-review"

# Design review (requires Playwright MCP)
claude "/design-review"
```

---

## Customization

Feel free to modify any templates to match your workflow. Common customizations:

- Add your design system tokens to `design-principles-example.md`
- Adjust review priorities in `pragmatic-code-review-subagent.md`
- Add custom security rules to `security-review-slash-command.md`
