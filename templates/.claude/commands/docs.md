---
name: docs
description: Generate or update project documentation
allowed-tools: Bash, Read, Edit, Glob, Grep, Write, TodoWrite
---

# Documentation Generator

You are helping the user create or update project documentation.

## Documentation Types

### 1. README.md
The main project documentation including:
- Project title and description
- Features list
- Installation instructions
- Usage examples
- Configuration options
- Contributing guidelines
- License

### 2. API Documentation
For backend projects:
- Endpoint descriptions
- Request/response formats
- Authentication requirements
- Error codes
- Examples with curl/fetch

### 3. Component Documentation
For frontend projects:
- Component props/interfaces
- Usage examples
- Storybook stories (if applicable)

### 4. Code Comments
- JSDoc/TSDoc for functions
- Docstrings for Python
- Inline comments for complex logic

## Process

### Step 1: Analyze Codebase
Scan the project to understand:
- Project structure
- Main entry points
- Public APIs/exports
- Configuration options
- Dependencies

### Step 2: Identify Gaps
Compare existing documentation against:
- Exported functions/components
- API endpoints
- Configuration options
- Setup requirements

### Step 3: Generate Documentation

**For README.md:**
```markdown
# Project Name

Brief description of what this project does.

## Features

- Feature 1
- Feature 2

## Installation

\`\`\`bash
npm install
\`\`\`

## Usage

\`\`\`javascript
// Example code
\`\`\`

## Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | 3000 |

## Contributing

1. Fork the repo
2. Create a branch
3. Make changes
4. Submit PR

## License

MIT
```

**For API endpoints:**
```markdown
## GET /api/users

Returns a list of users.

### Request

\`\`\`bash
curl -X GET https://api.example.com/users \
  -H "Authorization: Bearer TOKEN"
\`\`\`

### Response

\`\`\`json
{
  "users": [
    { "id": 1, "name": "John" }
  ]
}
\`\`\`
```

### Step 4: Review & Refine
- Ensure accuracy
- Add missing sections
- Fix formatting
- Update outdated info

## Options

- `/docs` - Generate/update all documentation
- `/docs readme` - Generate README.md
- `/docs api` - Generate API documentation
- `/docs [file]` - Document specific file/component
- `/docs --check` - Check for missing documentation

## Output

```
DOCUMENTATION UPDATED
=====================
Files modified:
- README.md (created/updated)
- docs/API.md (created/updated)
- src/components/Button.tsx (JSDoc added)

Coverage:
- Functions documented: 45/50 (90%)
- Endpoints documented: 12/12 (100%)
- Components documented: 8/10 (80%)

Suggestions:
- Add examples for `utils/helpers.ts`
- Document environment variables
```
