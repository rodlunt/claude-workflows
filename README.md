# Claude Workflows - Project Starter Templates

A template folder for starting new projects with Claude Code. Run the `/setup` wizard to generate a customized CLAUDE.md for your project.

## Quick Start

**Option 1: Interactive Setup (Recommended)**
```bash
# In your new project directory
claude "/setup"
```

**Option 2: Manual Setup**
1. Copy the templates folder contents to your project
2. Edit CLAUDE.md with your project specifics
3. Copy `.claude/commands/` for slash commands
4. Copy `.github/workflows/` for automated PR reviews

---

## Folder Structure

```
claude-workflows/
└── templates/
    ├── CLAUDE.md                    # Project config template
    ├── .claude/commands/            # Slash commands
    │   ├── setup.md                 # Interactive project wizard
    │   ├── review.md                # Code review (Pragmatic Quality)
    │   ├── security-review.md       # Security scan (OWASP-based)
    │   ├── design-review.md         # UI/UX review (Playwright)
    │   ├── test.md                  # Run tests and fix failures
    │   ├── deploy.md                # Deploy to staging/production
    │   └── docs.md                  # Generate documentation
    └── .github/workflows/           # GitHub Actions
        ├── code-review.yml          # Automated code review on PRs
        └── security-review.yml      # Automated security scan on PRs
```

---

## Available Slash Commands

| Command | Description |
|---------|-------------|
| `/setup` | Interactive project setup wizard |
| `/review` | Pragmatic code review (architecture, logic, security, tests) |
| `/security-review` | OWASP-based security scan (>80% confidence filter) |
| `/design-review` | UI/UX review (requires Playwright MCP) |
| `/test` | Run tests and fix any failures |
| `/deploy` | Deploy to staging or production |
| `/docs` | Generate or update documentation |

---

## What the Setup Wizard Configures

1. **Project Type & Features** - What you're building and what it needs
2. **Tech Stack** - Framework, backend, database, styling, testing
3. **Project Structure** - Folder organization
4. **Code Conventions** - TypeScript, naming, formatting, git style
5. **Commands** - Package manager and scripts
6. **Environment Variables** - Required secrets and config
7. **Testing & CI/CD** - Test strategy, coverage, pipeline
8. **Deployment** - Hosting platform, environments
9. **Review Workflows** - Code, security, design reviews
10. **MCP Servers** - Context7, Playwright, MUI, Mobile MCPs
11. **Git & GitHub** - Initialize repo, create GitHub remote

---

## GitHub Secrets Required

For automated PR reviews, add these secrets to your repository:

| Secret | Description |
|--------|-------------|
| `CLAUDE_CODE_OAUTH_TOKEN` | OAuth token for Claude Code Action |
| `ANTHROPIC_API_KEY` | API key for security review action |

---

## Recommended MCP Servers

| MCP | Purpose | Install Command |
|-----|---------|-----------------|
| **Context7** | Up-to-date library docs | `claude mcp add context7 -- npx -y @upstash/context7-mcp` |
| **Playwright** | Browser automation/testing | `claude mcp add playwright -- npx -y @playwright/mcp` |
| **MUI** | Material UI docs | `claude mcp add mui-mcp -- npx -y @mui/mcp@latest` |
| **Mobile MCP** | iOS/Android automation | `claude mcp add mobile-mcp -- npx -y @anthropic/mobile-mcp` |

---

## Review Frameworks

### Code Review (Pragmatic Quality)
- Balances engineering standards with development speed
- 7 priority levels: Architecture > Logic > Security > Performance > Tests > Style > Docs
- Triage: Critical/Blocker > Improvement > Nit

### Security Review
- OWASP-based vulnerability scanning
- Only flags issues with >80% exploit confidence
- Categories: Injection, Auth, Crypto, Code Execution, Data Exposure

### Design Review
- Live UI testing via Playwright screenshots
- Standards: Stripe, Airbnb, Linear quality
- WCAG 2.1 AA accessibility compliance
