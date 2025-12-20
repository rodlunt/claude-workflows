---
name: test
description: Run tests and fix any failures
allowed-tools: Bash, Read, Edit, Glob, Grep, Write, TodoWrite
---

# Test Runner

You are helping the user run tests and fix any failures.

## Process

### Step 1: Detect Test Framework

Check for test configuration files:
- `package.json` (scripts.test) → npm/yarn/pnpm test
- `vitest.config.*` → Vitest
- `jest.config.*` → Jest
- `pytest.ini` / `pyproject.toml` → pytest
- `Cargo.toml` → cargo test
- `go.mod` → go test

### Step 2: Run Tests

Execute the appropriate test command:

```bash
# JavaScript/TypeScript
npm test
# or: npm run test:unit, npm run test:e2e

# Python
pytest -v

# Go
go test ./...

# Rust
cargo test
```

### Step 3: Analyze Failures

For each failing test:
1. Read the test file to understand what's being tested
2. Read the source file being tested
3. Identify the root cause:
   - Logic error in source code?
   - Outdated test expectations?
   - Missing mock/stub?
   - Environment issue?

### Step 4: Fix Failures

- If source code is wrong → Fix the source code
- If test expectation is outdated → Update the test
- If test is flaky → Improve test reliability
- If missing dependency → Install and configure

### Step 5: Re-run Tests

After fixes, re-run tests to confirm:
- All tests pass
- No regressions introduced
- Coverage maintained

## Output

Provide a summary:
```
TEST RESULTS
============
Total:  [X] tests
Passed: [X] ✓
Failed: [X] ✗
Fixed:  [X] issues

Changes made:
- [file]: [description of fix]
```

## Options

The user can specify:
- `/test` - Run all tests
- `/test unit` - Run unit tests only
- `/test e2e` - Run E2E tests only
- `/test [filename]` - Run tests for specific file
- `/test --coverage` - Run with coverage report
