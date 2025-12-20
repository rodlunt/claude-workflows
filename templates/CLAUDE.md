# Project Name

> Brief description of what this project does.

## Tech Stack

- **Frontend:** [e.g., React, Vue, Next.js]
- **Backend:** [e.g., Node.js, Python, Go]
- **Database:** [e.g., PostgreSQL, MongoDB]
- **Styling:** [e.g., Tailwind CSS, styled-components]
- **Testing:** [e.g., Jest, Vitest, Playwright]

## Project Structure

```
src/
├── components/    # Reusable UI components
├── pages/         # Page components / routes
├── services/      # API calls and external services
├── utils/         # Helper functions
├── hooks/         # Custom React hooks (if applicable)
└── types/         # TypeScript types/interfaces
```

## Commands

```bash
# Development
npm run dev

# Build
npm run build

# Test
npm run test

# Lint
npm run lint
```

## Code Conventions

- Use TypeScript for all new files
- Follow existing naming patterns in the codebase
- Components use PascalCase, utilities use camelCase
- Keep functions small and focused
- Write tests for critical business logic

## Architecture Decisions

<!-- Document key decisions here -->
- [Decision 1]: [Reasoning]
- [Decision 2]: [Reasoning]

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | Database connection string | Yes |
| `API_KEY` | External API key | Yes |

## Review Checklist

When reviewing code, ensure:
- [ ] No hardcoded secrets or API keys
- [ ] Error handling is in place
- [ ] Types are properly defined
- [ ] Tests cover new functionality
- [ ] Responsive design (if UI changes)

## Design Principles

<!-- Reference your design system here -->
- Follow consistent spacing (4px, 8px, 16px, 24px, 32px)
- Use design tokens for colors
- Ensure WCAG 2.1 AA accessibility compliance
- Mobile-first responsive design
