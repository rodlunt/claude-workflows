---
name: setup
description: Interactive project setup wizard - creates a customized CLAUDE.md
---

# Project Setup Wizard

You are helping the user set up a new project. Walk through this process interactively, asking questions and confirming choices at each step.

## Your Approach

1. Be conversational and helpful
2. Offer recommendations with brief explanations
3. Let the user override any suggestion
4. Confirm before moving to the next section
5. At the end, generate a complete CLAUDE.md

---

## Step 1: Project Type & Features

Start by asking:

"What type of project are you building today?"

Options:
- Web App (Frontend only)
- Full-Stack Web App
- Backend/API Service
- Mobile App
- CLI Tool
- Library/Package
- Something else

Then ask: "What key features will this project need?"

Common features to offer (select all that apply):
- [ ] User authentication (login, signup, password reset)
- [ ] Database (CRUD operations, data models)
- [ ] API integration (external services)
- [ ] File uploads / media handling
- [ ] Real-time features (WebSockets, live updates)
- [ ] Payments / subscriptions
- [ ] Admin dashboard
- [ ] Search functionality
- [ ] Notifications (email, push)
- [ ] Analytics / tracking

Based on their answers, you'll tailor tech stack recommendations and CLAUDE.md content.

---

## Step 2: Tech Stack

For each relevant category, offer 2-3 options with trade-offs. Categories:

**Frontend:** Next.js, React+Vite, Vue, Svelte, etc.
**Backend:** Node.js, Python, Go, Rust, etc.
**Database:** PostgreSQL, MongoDB, SQLite, Supabase, etc.
**Styling:** Tailwind, CSS Modules, styled-components, shadcn/ui
**Testing:** Vitest, Jest, Playwright, pytest

Ask about each relevant category, explain your recommendation, and confirm their choice.

---

## Step 3: Project Structure

Propose a folder structure based on their stack. Ask if they want to adjust it.

---

## Step 4: Conventions

Confirm their preferences for:
- TypeScript or JavaScript
- Naming conventions
- Formatting (Prettier settings)
- Git commit style
- Any team-specific rules

---

## Step 5: Package Manager & Commands

Ask which they prefer: npm, yarn, pnpm, or bun

Confirm the standard commands (dev, build, test, lint).

---

## Step 6: Environment Variables

Ask what external services they'll use and build the env var list.

---

## Step 7: Final Review

Present a complete summary of all choices. Ask for confirmation.

---

## Step 8: Testing & CI/CD Setup

Ask: "How would you like to handle testing and continuous integration?"

### Testing Strategy

**1. What testing levels do you need?**
- [ ] Unit tests - Individual functions/components
- [ ] Integration tests - API routes, database operations
- [ ] E2E tests - Full user flows (requires Playwright)
- [ ] Visual regression - Screenshot comparisons

**2. Test runner preference?** (based on stack)
- JavaScript/TypeScript: Vitest (Recommended), Jest
- Python: pytest, unittest
- Go: built-in testing
- Rust: built-in testing

**3. Coverage requirements?**
- [ ] No minimum - Just critical paths
- [ ] 70%+ - Good coverage
- [ ] 90%+ - Comprehensive (enterprise)

### CI/CD Pipeline

**4. What should run on every PR?**
- [ ] Lint & format check
- [ ] Type checking (TypeScript)
- [ ] Unit tests
- [ ] Integration tests
- [ ] E2E tests
- [ ] Build verification
- [ ] Security scan
- [ ] Code review (Claude)

**5. What should run on merge to main?**
- [ ] All PR checks
- [ ] Deploy to staging
- [ ] Deploy to production
- [ ] Release tagging

Based on answers, generate `.github/workflows/ci.yml` with appropriate jobs.

---

## Step 9: Deployment Setup

Ask: "Where will this project be deployed?"

### Deployment Target

**1. Hosting platform?**
- [ ] **Vercel** - Best for Next.js, React (Recommended for frontend)
- [ ] **Railway** - Easy full-stack deployment
- [ ] **AWS** - Maximum control (ECS, Lambda, S3)
- [ ] **Google Cloud** - GCP services (Cloud Run, Firebase)
- [ ] **Docker** - Self-hosted / any platform
- [ ] **Fly.io** - Edge deployment
- [ ] **Self Hosted** - On own server
- [ ] **Other** - Specify

**2. Environment tiers?**
- [ ] Production only
- [ ] Production + Staging
- [ ] Production + Staging + Development

**3. Database hosting?** (if applicable)
- [ ] **Supabase** - Postgres + Auth + Realtime
- [ ] **PlanetScale** - MySQL, branching
- [ ] **Neon** - Serverless Postgres
- [ ] **MongoDB Atlas** - Document database
- [ ] **AWS RDS** - Managed SQL
- [ ] **Self-hosted** - Docker/VM

Based on answers:
- Generate deployment configs (vercel.json, Dockerfile, etc.)
- Add deploy scripts to package.json
- Create environment variable templates

---

## Step 10: Review Workflows Setup

Ask: "Would you like to set up automated review workflows?"

### Questions to Ask:

**1. Which review types do you want?**
- [ ] Code Review - Architecture, logic, security, tests, performance
- [ ] Security Review - Vulnerability scanning (OWASP-based)
- [ ] Design Review - UI/UX, accessibility, responsiveness (requires Playwright)

**2. How do you want to trigger reviews?**
- [ ] **Slash commands** (`/review`, `/security-review`, `/design-review`) - Manual, on-demand
- [ ] **GitHub Actions** - Automatic on every PR
- [ ] **Both** (Recommended)

**3. Code review strictness?**
- [ ] **Startup mode** - Balance speed with quality, focus on blockers only
- [ ] **Enterprise mode** - Strict standards, comprehensive coverage

**4. Security review sensitivity?**
- [ ] **High confidence only** (>80%) - Fewer false positives (Recommended)
- [ ] **Medium + High** - More findings, some may be theoretical

**5. Design standards reference?**
- [ ] **S-Tier SaaS** (Stripe/Airbnb/Linear style) - Included by default
- [ ] **Custom** - Point to your own design system docs

**6. Reference websites for design inspiration?** (if Design Review selected)

Ask: "Are there any websites you'd like Playwright to analyze for design guidance?"

Examples to suggest:
- A competitor's app you admire
- Your company's existing products
- Design inspiration sites (Dribbble, Behance)
- Industry leaders (stripe.com, linear.app, notion.so)

If provided, Claude will:
- Use Playwright to visit and screenshot the reference sites
- Extract design patterns, colors, typography, spacing
- Use these as guidance when reviewing your designs

### Based on Answers:

- If **GitHub Actions** selected: Copy workflow files to `.github/workflows/`
- If **Design Review** selected: Ensure Playwright MCP is installed
- If **Custom design standards**: Ask for path to design docs

---

## Step 11: MCP Server Setup

Ask: "Would you like to set up MCP servers for enhanced capabilities?"

Based on their tech stack, recommend relevant MCPs:

### Always Recommend:
- **Context7** - Up-to-date library documentation in your prompts
  ```bash
  claude mcp add context7 -- npx -y @upstash/context7-mcp
  ```

### For Web Projects (Frontend/Full-Stack):
- **Playwright** - Browser automation and testing
  ```bash
  claude mcp add playwright -- npx -y @playwright/mcp
  ```

### For Material UI Projects:
- **MUI MCP** - Material UI component docs and best practices
  ```bash
  claude mcp add mui-mcp -- npx -y @mui/mcp@latest
  ```

### For Android Projects:
- **Mobile MCP** - Cross-platform mobile automation
  ```bash
  claude mcp add mobile-mcp -- npx -y @anthropic/mobile-mcp
  ```
- **ADB MCP** - Android device control via ADB
  ```bash
  claude mcp add adb -- npx -y android-mcp-server
  ```

Ask which MCPs they want installed, then run the commands.

---

## Step 12: Generate Files

Once confirmed:
1. Create the CLAUDE.md file in the project root
2. Offer to copy the GitHub Actions workflows for automated reviews

---

## Step 13: Git & GitHub Setup

Ask: "Would you like me to set up a Git repository and create a GitHub repo?"

If yes, ask:
- **Repository name:** (suggest based on project folder name)
- **Visibility:** Public or Private?
- **Description:** One-line description for GitHub

Then execute:

```bash
# Initialize local repo
git init

# Create .gitignore based on their tech stack
# (Node: node_modules, .env, dist, etc.)
# (Python: venv, __pycache__, .env, etc.)

# Initial commit
git add .
git commit -m "Initial commit - project setup"

# Create GitHub repo and push
gh repo create [repo-name] --[public/private] --source=. --push --description "[description]"
```

Confirm success and provide the GitHub URL.

---

## Step 14: Final Summary

Present what was created:
- CLAUDE.md configured
- Testing: [Vitest/Jest/pytest] with [coverage level]
- CI/CD: `.github/workflows/ci.yml`
- Deployment: [Vercel/Railway/Docker/etc.] configured
- Review workflows: [Code / Security / Design]
- MCP servers: [Context7, Playwright, etc.]
- .gitignore for their stack
- Git repo initialized
- GitHub repo: `https://github.com/[username]/[repo]`

Remind them of available slash commands:

| Command | What It Does |
|---------|--------------|
| `/setup` | Run this wizard again for new projects |
| `/review` | Code review before merging |
| `/security-review` | Security vulnerability scan |
| `/design-review` | UI/UX review (requires Playwright) |
| `/test` | Run tests and fix failures |
| `/deploy` | Deploy to staging/production |
| `/docs` | Generate/update documentation |

Also mention:
- "use context7" in prompts for up-to-date library docs
- Update CLAUDE.md as the project evolves

Be encouraging and wish them luck with their project!
