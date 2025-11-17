# CLAUDE.md - AI Assistant Guide

This document provides comprehensive guidance for AI assistants working with this repository. It explains the codebase structure, development workflows, and key conventions to follow.

**Last Updated:** 2025-11-17
**Repository:** TutorialPlaywright
**Current State:** Documentation/Educational Phase

---

## Table of Contents

1. [Repository Overview](#repository-overview)
2. [Current State & Architecture](#current-state--architecture)
3. [Development Workflow](#development-workflow)
4. [Git Conventions](#git-conventions)
5. [File Structure](#file-structure)
6. [Documentation Standards](#documentation-standards)
7. [Key Patterns & Conventions](#key-patterns--conventions)
8. [Common Tasks for AI Assistants](#common-tasks-for-ai-assistants)
9. [Future Development](#future-development)
10. [Important Reminders](#important-reminders)

---

## Repository Overview

### Purpose
This repository serves as a **Playwright tutorials and best practices** resource, currently in the documentation phase. It's designed to:
- Provide comprehensive guides for Git + VSCode workflows
- Share development best practices with teams
- Serve as a foundation for future Playwright tutorials and examples

### Target Audience
- Development teams using Azure DevOps (ADO)
- Engineers learning Git workflows with VSCode
- Future: Developers learning Playwright test automation

### Current State
**Phase:** Documentation and Foundation Building
**Status:** Active Documentation Development
**Technology Stack:** None implemented yet (documentation only)

---

## Current State & Architecture

### What Exists Now

```
TutorialPlaywright/
├── .git/                               # Git version control
├── README.md                           # Repository entry point
├── GIT_VSCODE_BEST_PRACTICES.md       # Comprehensive Git/VSCode guide
└── CLAUDE.md                           # This file - AI assistant guide
```

### What's NOT Implemented Yet

The repository name suggests Playwright content, but currently has:
- ❌ No Playwright installation
- ❌ No Node.js/npm setup (`package.json` missing)
- ❌ No test files or test configurations
- ❌ No source code directories
- ❌ No build configurations
- ❌ No CI/CD pipelines
- ❌ No `.gitignore` file

### Technology References

While not implemented, the documentation references:
- **Git** - Version control (actively used)
- **VSCode** - Primary IDE
- **Azure DevOps** - Repository hosting and PR management
- **Node.js/npm** - Mentioned for future use
- **Playwright** - Intended future focus

---

## Development Workflow

### Branch Strategy

**Current Branch:** `claude/claude-md-mi3suhx7v9i4bcs0-01Ck95pqQLJfQa12gxk6GC9z`

#### Branch Naming Convention

Follow these patterns as documented in `GIT_VSCODE_BEST_PRACTICES.md`:

```
feature/descriptive-name       # New features
bugfix/issue-description       # Bug fixes
hotfix/critical-fix           # Urgent production fixes
refactor/component-name       # Code refactoring
docs/topic-name              # Documentation updates
```

**Examples:**
- ✅ `feature/add-playwright-config`
- ✅ `docs/update-contributing-guide`
- ✅ `bugfix/fix-broken-links`

**Special Convention for AI Assistants:**
- AI-created branches typically use pattern: `claude/claude-md-{session-id}`
- These branches are temporary and session-specific

### Commit Message Format

Follow the conventional commits standard:

```
<type>: <short summary>

<optional detailed description>

<optional footer>
```

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `refactor:` - Code refactoring (no functionality change)
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks
- `style:` - Code style/formatting changes

**Examples:**
```bash
✅ docs: Add comprehensive Git + VSCode best practices guide
✅ feat: Add Playwright configuration and initial test setup
✅ fix: Correct broken links in README
✅ chore: Update dependencies to latest versions

❌ Fix stuff
❌ Updates
❌ WIP
```

### Pull Request Process

Based on `GIT_VSCODE_BEST_PRACTICES.md`, follow these PR guidelines:

1. **Keep PRs Small:** Aim for 200-400 lines of changes
2. **One Feature Per PR:** Don't combine multiple unrelated changes
3. **Write Clear Descriptions:** Use the PR template below
4. **Request Appropriate Reviewers:** Include code owners and subject matter experts
5. **Respond to Feedback Promptly:** Address all review comments

**PR Description Template:**
```markdown
## Summary
[Brief description of what this PR does]

## Changes Made
- [Change 1]
- [Change 2]
- [Change 3]

## Testing Done
- [Test 1]
- [Test 2]

## Related Work Items
- Fixes #[issue number]
- Related to #[issue number]

## Checklist
- [ ] Documentation updated
- [ ] No merge conflicts
- [ ] Follows repository conventions
```

---

## Git Conventions

### Working with Git in This Repository

#### Initial Setup
```bash
# Verify Git configuration
git config --list

# Ensure correct user details
git config --global user.name "Your Name"
git config --global user.email "your.email@company.com"
```

#### Daily Workflow
```bash
# 1. Start work - ensure you're on correct branch
git status
git branch

# 2. Make changes and commit frequently
git add .
git commit -m "docs: Add section on XYZ"

# 3. Push to remote
git push -u origin branch-name
```

#### Syncing with Main Branch
```bash
# Fetch latest changes
git fetch origin

# Option 1: Rebase (cleaner history - preferred)
git rebase origin/main

# Option 2: Merge (preserves history)
git merge origin/main

# After rebase, force push with safety
git push --force-with-lease
```

### Important Git Rules

1. **Never force push to main/master**
2. **Always use `--force-with-lease` instead of `--force`**
3. **Never commit sensitive data** (API keys, passwords, tokens)
4. **Commit frequently** with logical units of work
5. **Pull before push** to avoid conflicts
6. **Test before pushing** (when tests exist)

---

## File Structure

### Current Files

#### `/README.md`
**Purpose:** Repository entry point
**Contents:**
- Repository overview
- Links to available guides
- Getting started information

**When to Update:**
- Adding new documentation files
- Changing repository purpose
- Adding new sections or guides

#### `/GIT_VSCODE_BEST_PRACTICES.md`
**Purpose:** Comprehensive Git + VSCode workflow guide
**Contents:**
- Complete Git workflow tutorials
- VSCode integration instructions
- 10+ common scenarios with solutions
- Azure DevOps PR creation process
- Troubleshooting section
- Quick reference commands

**Size:** ~22KB, 1,054 lines
**Target Audience:** Developers using Git + VSCode + Azure DevOps

**When to Update:**
- Adding new Git scenarios
- Updating ADO processes
- Adding VSCode tips
- Correcting outdated information

#### `/CLAUDE.md` (This File)
**Purpose:** Guide for AI assistants working with this repository
**Contents:**
- Codebase structure explanation
- Development workflow guidelines
- Conventions and patterns
- Task guidance for AI assistants

**When to Update:**
- Significant repository structure changes
- New conventions adopted
- New technologies added
- Process updates

### Expected Future Files

When this repository evolves to include Playwright content:

```
package.json                    # Node.js dependencies and scripts
playwright.config.js           # Playwright configuration
.gitignore                     # Git ignore rules
tsconfig.json                  # TypeScript configuration (if using TS)
.nvmrc                         # Node version specification

tests/                         # Test files
  ├── e2e/                    # End-to-end tests
  ├── integration/            # Integration tests
  └── fixtures/               # Test fixtures

pages/                         # Page Object Model files (if using POM)
  └── LoginPage.js

utils/                         # Utility functions
  └── helpers.js

.github/                       # GitHub Actions (if migrating from ADO)
  └── workflows/
      └── playwright.yml

docs/                          # Additional documentation
  └── CONTRIBUTING.md
```

---

## Documentation Standards

### Writing Style

**Tone:**
- Clear and concise
- Professional but approachable
- Educational and helpful
- Action-oriented

**Formatting:**
- Use markdown for all documentation
- Include code examples in fenced code blocks
- Use tables for comparison information
- Include a table of contents for long documents (>500 lines)

### Documentation Structure

Every significant markdown file should include:

1. **Title** - Clear, descriptive H1 heading
2. **Table of Contents** - For documents >300 lines
3. **Introduction** - What this document covers
4. **Main Sections** - Well-organized with H2/H3 headings
5. **Examples** - Code samples and use cases
6. **References** - Links to related resources
7. **Metadata** - Version, last updated date, maintainer

### Code Examples

Always include:
- **Language identifier** in code blocks
- **Comments** for complex operations
- **Context** before the code block
- **Expected output** when relevant

**Example:**
```bash
# Pull latest changes from main branch
git pull origin main

# Expected output:
# From https://dev.azure.com/org/project/_git/repo
#  * branch            main       -> FETCH_HEAD
# Already up to date.
```

### Updating Documentation

**When updating existing docs:**
1. Read the entire document first
2. Maintain consistent style and tone
3. Update the "Last Updated" date
4. Update table of contents if adding sections
5. Test all code examples
6. Update related files if necessary (e.g., README links)

---

## Key Patterns & Conventions

### Naming Conventions

**Files:**
- Use `UPPERCASE.md` for top-level documentation (README.md, CLAUDE.md)
- Use `UPPERCASE_SNAKE_CASE.md` for multi-word docs (GIT_VSCODE_BEST_PRACTICES.md)
- Use `lowercase-kebab-case.js` for code files (when implemented)

**Branches:**
- `feature/lowercase-kebab-case`
- `bugfix/issue-description`
- `docs/topic-name`

**Commits:**
- Conventional commits format
- Imperative mood ("Add" not "Added")
- Start with lowercase (except proper nouns)

### Best Practices from GIT_VSCODE_BEST_PRACTICES.md

AI assistants should be aware of these key practices:

1. **Commit Frequently**
   - Small, logical units of work
   - Each commit should be complete and working

2. **Write Descriptive Messages**
   - Explain "why" not just "what"
   - Reference issues/work items

3. **Keep PRs Focused**
   - One feature/fix per PR
   - Easier to review and merge

4. **Test Before Committing**
   - Run tests if they exist
   - Verify code builds
   - Check for linting errors

5. **Protect Sensitive Data**
   - Never commit secrets
   - Use environment variables
   - Add sensitive files to `.gitignore`

6. **Use .gitignore Properly**
   ```gitignore
   node_modules/
   .env
   .env.local
   .vscode/
   .idea/
   dist/
   build/
   *.log
   .DS_Store
   Thumbs.db
   ```

---

## Common Tasks for AI Assistants

### 1. Adding New Documentation

**When asked to create new documentation:**

```bash
# 1. Ensure you're on the correct branch
git status

# 2. Create the documentation file
# (Use Write tool)

# 3. Update README.md with link to new doc

# 4. Commit with proper message
git add README.md new-documentation.md
git commit -m "docs: Add [topic] documentation"

# 5. Push changes
git push -u origin branch-name
```

**Checklist:**
- [ ] File follows naming conventions
- [ ] Includes table of contents (if long)
- [ ] Uses proper markdown formatting
- [ ] README.md updated with link
- [ ] Commit message follows conventions
- [ ] All links are valid

### 2. Updating Existing Documentation

**When asked to update documentation:**

```bash
# 1. Read the entire document first
# (Use Read tool)

# 2. Make updates maintaining style/tone
# (Use Edit tool)

# 3. Update "Last Updated" date

# 4. Commit with descriptive message
git add file.md
git commit -m "docs: Update [specific section] in [file]"

# 5. Push changes
git push
```

**Important:**
- Maintain existing style and tone
- Don't remove content without confirmation
- Update related files if necessary
- Verify all code examples still work

### 3. Setting Up Playwright (Future Task)

**When asked to add Playwright setup:**

```bash
# 1. Initialize npm project
npm init -y

# 2. Install Playwright
npm install -D @playwright/test

# 3. Initialize Playwright
npx playwright install

# 4. Create playwright.config.js
# (Use Write tool)

# 5. Create .gitignore
# (Use Write tool - include node_modules, test-results, etc.)

# 6. Create initial test structure
mkdir -p tests/e2e

# 7. Update README.md with setup instructions

# 8. Commit all changes
git add .
git commit -m "feat: Add Playwright test framework setup"
```

### 4. Creating or Updating CONTRIBUTING.md

**When establishing contribution guidelines:**

Include these sections:
- Branch naming conventions
- Commit message format
- PR process and template
- Code review guidelines
- Testing requirements
- Documentation standards
- Contact information

Reference `GIT_VSCODE_BEST_PRACTICES.md` for detailed Git workflows.

### 5. Analyzing Repository State

**When asked about repository structure:**

Use these commands:
```bash
# View file structure
ls -la

# Check Git status
git status

# View recent commits
git log --oneline -10

# View all branches
git branch -a

# Check for package.json (project setup)
ls package.json

# Check for test files
find . -name "*.test.js" -o -name "*.spec.js"
```

### 6. Responding to "What should I work on?"

**Suggested priorities based on current state:**

1. **Documentation Completeness**
   - Add CONTRIBUTING.md
   - Create Playwright tutorials
   - Add architecture documentation

2. **Project Setup**
   - Add package.json
   - Install Playwright
   - Create playwright.config.js
   - Add .gitignore

3. **Testing Infrastructure**
   - Create test directory structure
   - Add example test files
   - Set up CI/CD pipeline

4. **Code Examples**
   - Page Object Model examples
   - API testing examples
   - Visual regression examples

---

## Future Development

### Planned Enhancements

Based on the repository name and current state, expected future development:

#### Phase 1: Basic Setup
- [ ] Add `package.json` and install Playwright
- [ ] Create `playwright.config.js`
- [ ] Add `.gitignore` file
- [ ] Set up basic project structure

#### Phase 2: Testing Framework
- [ ] Create test directory structure
- [ ] Add example test files
- [ ] Implement Page Object Model pattern
- [ ] Add test utilities and helpers

#### Phase 3: CI/CD Integration
- [ ] Set up Azure DevOps pipeline
- [ ] Configure automated test runs
- [ ] Add test reporting
- [ ] Set up branch protection rules

#### Phase 4: Documentation Expansion
- [ ] Add Playwright tutorial series
- [ ] Create API testing guides
- [ ] Add troubleshooting documentation
- [ ] Create video tutorials (links)

#### Phase 5: Advanced Features
- [ ] Visual regression testing
- [ ] Performance testing examples
- [ ] Accessibility testing integration
- [ ] Mobile testing examples

### Technology Decisions to Make

When implementing Playwright:
- **Language:** JavaScript vs TypeScript
- **Test Organization:** Flat structure vs nested
- **Page Objects:** Yes/No, which pattern
- **Reporters:** Which reporters to enable
- **Browsers:** Which browsers to test
- **Parallelization:** Worker configuration

---

## Important Reminders

### For AI Assistants Working on This Repository

#### Always:
✅ **Read before writing** - Use Read tool before Edit/Write
✅ **Follow conventions** - Match existing patterns and style
✅ **Commit properly** - Use conventional commit messages
✅ **Update related files** - README when adding new docs
✅ **Test examples** - Verify all code examples work
✅ **Ask for clarification** - When requirements are unclear
✅ **Maintain consistency** - Match tone and structure
✅ **Document changes** - Update "Last Updated" dates

#### Never:
❌ **Force push to main** - Always work on feature branches
❌ **Skip reading docs** - Don't assume, read first
❌ **Break existing content** - Preserve working examples
❌ **Commit secrets** - No API keys, passwords, tokens
❌ **Ignore conventions** - Follow established patterns
❌ **Create unnecessary files** - Only create when needed
❌ **Use emojis** - Unless explicitly requested by user
❌ **Make assumptions** - Ask when uncertain

### Working with Git

**Current Branch:** `claude/claude-md-mi3suhx7v9i4bcs0-01Ck95pqQLJfQa12gxk6GC9z`

**Important Git Notes:**
- Always push to the current branch with: `git push -u origin branch-name`
- Branch names for AI work must start with `claude/` and match session ID
- Retry failed pushes up to 4 times with exponential backoff (2s, 4s, 8s, 16s)
- Use `--force-with-lease` instead of `--force` when necessary

### Understanding the Documentation

**Primary Resource:** `GIT_VSCODE_BEST_PRACTICES.md`
- Comprehensive (1,054 lines)
- Covers 10+ common scenarios
- Includes troubleshooting
- Has quick reference section

**When helping users:**
1. Reference specific sections from GIT_VSCODE_BEST_PRACTICES.md
2. Provide file:line references (e.g., GIT_VSCODE_BEST_PRACTICES.md:219)
3. Suggest relevant scenarios from the guide
4. Link to appropriate sections

### Context Awareness

**Remember:**
- This is a **documentation-first** repository
- **No code exists yet** - it's in planning phase
- **Azure DevOps** is the platform (not GitHub)
- **VSCode** is the primary IDE
- **Educational purpose** - clarity over brevity

---

## Quick Reference

### File Locations

| File | Purpose | Lines | Last Updated |
|------|---------|-------|--------------|
| README.md | Repository entry point | 16 | 2025-11-17 |
| GIT_VSCODE_BEST_PRACTICES.md | Git workflow guide | 1,054 | 2025-11-17 |
| CLAUDE.md | AI assistant guide | This file | 2025-11-17 |

### Key Commands

```bash
# Check current state
git status
git branch

# Start new work
git checkout -b feature/new-feature
git pull origin main

# Make changes
git add .
git commit -m "type: description"
git push -u origin feature/new-feature

# Sync with main
git fetch origin
git rebase origin/main
git push --force-with-lease
```

### Important Conventions

| Convention | Format | Example |
|------------|--------|---------|
| Branch naming | type/description | `feature/add-playwright`, `docs/update-readme` |
| Commit messages | type: description | `docs: Add section on testing` |
| File names (docs) | UPPERCASE_SNAKE.md | `GIT_VSCODE_BEST_PRACTICES.md` |
| Code files (future) | lowercase-kebab.js | `page-object.js` |

### Common Scenarios Reference

See `GIT_VSCODE_BEST_PRACTICES.md` for detailed solutions:

| Scenario | Location | Quick Answer |
|----------|----------|--------------|
| Adding changes to PR | Lines 305-335 | Commit and push to same branch |
| Syncing with main | Lines 338-393 | Rebase or merge main into branch |
| Merge conflicts | Lines 396-435 | Use VSCode visual resolver |
| Undo uncommitted | Lines 438-463 | `git restore .` |
| Amend last commit | Lines 466-484 | `git commit --amend` |
| Multiple branches | Lines 489-522 | Use `git stash` |
| Delete branches | Lines 610-634 | `git branch -d branch-name` |

---

## Conclusion

This repository is currently a **documentation and best practices hub** with plans to become a comprehensive Playwright tutorial resource.

**Current Focus:**
- Maintaining high-quality Git/VSCode documentation
- Establishing clear conventions and patterns
- Building foundation for future Playwright content

**AI Assistant Role:**
- Help maintain and expand documentation
- Follow established conventions strictly
- Suggest improvements when appropriate
- Prepare for future Playwright implementation

**Key Success Factors:**
1. **Consistency** - Follow existing patterns
2. **Clarity** - Write for educational purposes
3. **Accuracy** - Test all examples
4. **Completeness** - Don't leave gaps
5. **Maintenance** - Keep documentation current

---

**Document Metadata:**
- **Version:** 1.0.0
- **Created:** 2025-11-17
- **Last Updated:** 2025-11-17
- **Maintained By:** AI Assistants + Development Team
- **Review Cycle:** Update when significant changes occur

For questions or clarifications about this guide, refer to the commit history or ask the repository maintainers.
