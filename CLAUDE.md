# CLAUDE.md - AI Assistant Guide for Vigil

This document provides comprehensive guidance for AI assistants working with the Vigil codebase.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Development Workflow](#development-workflow)
4. [Key Conventions](#key-conventions)
5. [Common Tasks](#common-tasks)
6. [Testing Guidelines](#testing-guidelines)
7. [Code Quality Standards](#code-quality-standards)
8. [Troubleshooting](#troubleshooting)

---

## Project Overview

**Project Name:** Vigil

**Status:** New/In Development

**Description:** [To be updated as the project evolves]

### Tech Stack

[To be updated based on project requirements]

- **Language(s):** TBD
- **Framework(s):** TBD
- **Build Tool:** TBD
- **Package Manager:** TBD
- **Testing Framework:** TBD

### Key Dependencies

[To be updated when dependencies are added]

---

## Repository Structure

```
vigil/
├── .git/              # Git version control
├── CLAUDE.md          # This file - AI assistant guide
├── README.md          # Project documentation (to be created)
└── [Project files to be added]
```

### Directory Conventions

As the project grows, follow these organizational principles:

- **Source Code:** Place in `src/` or language-appropriate directory
- **Tests:** Place in `tests/`, `__tests__/`, or alongside source files with `.test.*` or `.spec.*` suffix
- **Configuration:** Keep config files at the root or in a `config/` directory
- **Documentation:** Place in `docs/` or use markdown files at root
- **Build Artifacts:** Configure to output to `dist/`, `build/`, or similar
- **Scripts:** Place in `scripts/` or `bin/`

---

## Development Workflow

### Branch Strategy

- **Main Branch:** `main` or `master` (to be determined on first commit)
- **Feature Branches:** Use prefix `feature/` or `claude/` for AI-assisted development
  - Example: `claude/claude-md-mipe1oj1ay4qskda-01VkTcB9Hc8AdEVQSWhcjdLP`
- **Bug Fix Branches:** Use prefix `fix/` or `bugfix/`
- **Hotfix Branches:** Use prefix `hotfix/`

### Commit Message Convention

Use clear, descriptive commit messages following these guidelines:

```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, no logic change)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks, dependency updates
- `perf`: Performance improvements

**Examples:**
```
feat: add user authentication module

Implements JWT-based authentication with refresh tokens.
Includes middleware for protected routes.

Closes #123
```

```
fix: resolve race condition in data loader

The loader was not properly awaiting async operations,
causing intermittent failures.
```

### Pull Request Guidelines

1. **Title:** Clear, descriptive title summarizing the change
2. **Description:** Include:
   - Summary of changes (2-3 bullet points)
   - Motivation/context
   - Testing performed
   - Any breaking changes
3. **Review:** Ensure code is tested and documented before requesting review
4. **Merge:** Squash and merge for cleaner history (or follow project preference)

---

## Key Conventions

### Code Style

**General Principles:**
- Write clear, self-documenting code
- Prefer readability over cleverness
- Keep functions small and focused
- Use meaningful variable and function names
- Avoid deep nesting (max 3-4 levels)

**Naming Conventions:**
- Variables/Functions: `camelCase` (JavaScript/TypeScript) or `snake_case` (Python/Rust)
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`
- Files: Lowercase with hyphens (`user-service.ts`) or match class name (`UserService.ts`)

**Comments:**
- Add comments for complex logic, not obvious code
- Use JSDoc/docstrings for public APIs
- Keep comments up-to-date with code changes
- Avoid redundant comments that repeat what code does

### Error Handling

- Always handle errors explicitly
- Use try-catch for synchronous errors
- Use proper error handling for async operations
- Provide meaningful error messages
- Log errors with context
- Don't silently swallow errors

### Security Best Practices

- Never commit secrets, API keys, or credentials
- Use environment variables for sensitive data
- Validate and sanitize all user input
- Implement proper authentication and authorization
- Follow OWASP guidelines for web security
- Keep dependencies updated

---

## Common Tasks

### Initial Setup

```bash
# Clone the repository
git clone <repository-url>
cd vigil

# [Install dependencies - command TBD based on tech stack]
# npm install
# pip install -r requirements.txt
# cargo build
```

### Running the Project

```bash
# [Development server - command TBD]
# npm run dev
# python main.py
# cargo run
```

### Running Tests

```bash
# [Test command - TBD]
# npm test
# pytest
# cargo test
```

### Building for Production

```bash
# [Build command - TBD]
# npm run build
# python setup.py build
# cargo build --release
```

### Code Formatting

```bash
# [Format command - TBD]
# npm run format
# black .
# cargo fmt
```

### Linting

```bash
# [Lint command - TBD]
# npm run lint
# pylint src/
# cargo clippy
```

---

## Testing Guidelines

### Testing Strategy

- **Unit Tests:** Test individual functions and modules in isolation
- **Integration Tests:** Test interactions between components
- **End-to-End Tests:** Test complete user workflows
- **Test Coverage:** Aim for >80% coverage for critical paths

### Writing Tests

**Test Structure:**
```
describe/test("what is being tested", () => {
  // Arrange: Set up test data and conditions

  // Act: Execute the code being tested

  // Assert: Verify the results
})
```

**Best Practices:**
- Each test should test one thing
- Tests should be independent and isolated
- Use descriptive test names
- Mock external dependencies
- Test edge cases and error conditions
- Keep tests fast and deterministic

### Test File Organization

- Place tests near the code they test or in a dedicated `tests/` directory
- Use naming convention: `*.test.*` or `*.spec.*`
- Mirror source code structure in test directory

---

## Code Quality Standards

### Before Committing

- [ ] Code runs without errors
- [ ] All tests pass
- [ ] Code is formatted according to project style
- [ ] No linting errors
- [ ] Documentation is updated
- [ ] No commented-out code (unless temporarily needed)
- [ ] No debug statements or console.logs
- [ ] No unnecessary dependencies added

### Code Review Checklist

- [ ] Code is clear and maintainable
- [ ] Follows project conventions
- [ ] Handles errors appropriately
- [ ] Includes tests for new functionality
- [ ] No security vulnerabilities introduced
- [ ] Performance considerations addressed
- [ ] Documentation updated
- [ ] Breaking changes documented

### Performance Guidelines

- Avoid premature optimization
- Profile before optimizing
- Consider time and space complexity
- Cache expensive operations when appropriate
- Use lazy loading for large resources
- Minimize network requests
- Optimize database queries

---

## Troubleshooting

### Common Issues

**Issue:** [To be documented as issues are encountered]
**Solution:** [Solutions to common problems]

### Debug Strategies

1. **Read error messages carefully** - They often tell you exactly what's wrong
2. **Check recent changes** - Use `git diff` to see what changed
3. **Isolate the problem** - Reduce to minimal reproducible example
4. **Use debugging tools** - Debugger, logging, profiling
5. **Search documentation** - Check official docs first
6. **Search issues** - Check project issues and Stack Overflow
7. **Ask for help** - Provide context, what you've tried, and error messages

### Useful Commands

```bash
# View recent commits
git log --oneline -10

# See what changed
git diff

# Check current branch and status
git status

# Stash current changes
git stash

# Create and switch to new branch
git checkout -b branch-name

# View git history for a file
git log -p <file>

# Find when a bug was introduced
git bisect
```

---

## AI Assistant Guidelines

### When Working on This Project

1. **Always read before modifying** - Read existing code before making changes
2. **Use the TodoWrite tool** - Track multi-step tasks for transparency
3. **Make minimal changes** - Only change what's necessary
4. **Test your changes** - Run tests before committing
5. **Follow conventions** - Match existing code style and patterns
6. **Document as you go** - Update this file when you discover new patterns
7. **Commit logically** - Make atomic commits with clear messages
8. **Push to correct branch** - Always push to `claude/*` branches as specified

### File Operations

- **Prefer Edit over Write** - Modify existing files rather than recreating them
- **Read first** - Always read a file before editing it
- **Use specialized tools** - Use Read/Edit/Write instead of bash commands
- **Preserve formatting** - Match existing indentation and style

### Common Pitfalls to Avoid

- Don't create unnecessary abstraction
- Don't add features beyond what's requested
- Don't refactor unrelated code
- Don't add dependencies without considering alternatives
- Don't commit commented-out code
- Don't skip error handling
- Don't ignore test failures
- Don't make assumptions - verify by reading code

### Project-Specific Notes

[To be updated with project-specific guidance as patterns emerge]

- Preferred patterns: [TBD]
- Anti-patterns to avoid: [TBD]
- Special considerations: [TBD]

---

## Updating This Document

This CLAUDE.md file should be treated as a living document. Update it when:

- Project structure changes significantly
- New conventions are established
- Common issues and solutions are identified
- New tools or workflows are adopted
- Dependencies or tech stack changes

Keep this document accurate and useful for both AI assistants and human developers.

---

**Last Updated:** 2025-12-03
**Version:** 1.0.0
**Status:** Initial version for new repository
