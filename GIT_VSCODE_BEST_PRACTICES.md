# Git + VSCode Best Practices Guide

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Starting Development in a New Branch from Main](#starting-development-in-a-new-branch-from-main)
3. [Making Changes and Commits](#making-changes-and-commits)
4. [Pushing Your Branch to ADO](#pushing-your-branch-to-ado)
5. [Creating a Pull Request in Azure DevOps](#creating-a-pull-request-in-azure-devops)
6. [Common Scenarios](#common-scenarios)
7. [Best Practices](#best-practices)
8. [Troubleshooting](#troubleshooting)

---

## Prerequisites

### Required Tools
- **Visual Studio Code** (latest version)
- **Git** installed on your machine
- **Azure DevOps** account with repository access

### VSCode Extensions (Recommended)
- **GitLens** - Supercharge Git capabilities
- **Azure Repos** - Azure DevOps integration
- **Git Graph** - Visualize branch history
- **Git History** - View git log and file history

### Initial Setup
1. Configure Git username and email (first-time setup):
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@company.com"
```

2. Verify configuration:
```bash
git config --list
```

---

## Starting Development in a New Branch from Main

### Step 1: Ensure You're on Main Branch
1. Open **Source Control** panel in VSCode (`Ctrl+Shift+G` or `Cmd+Shift+G` on Mac)
2. Click on the branch name at the bottom-left corner of VSCode
3. Select `main` from the dropdown (or `master` depending on your repository)

**Using Terminal:**
```bash
git checkout main
```

### Step 2: Pull Latest Changes from Main
Before creating a new branch, always sync with the remote main branch:

**Using VSCode:**
1. Click the "..." menu in Source Control panel
2. Select **Pull** (or **Pull from...**)

**Using Terminal:**
```bash
git pull origin main
```

### Step 3: Create a New Branch
Branch naming conventions matter! Use descriptive names:
- `feature/user-authentication`
- `bugfix/login-error`
- `hotfix/critical-security-patch`
- `refactor/api-endpoints`

**Using VSCode:**
1. Click on branch name (bottom-left)
2. Select **Create new branch...**
3. Enter your branch name (e.g., `feature/add-payment-integration`)
4. Press Enter

**Using Terminal:**
```bash
# Create and switch to new branch
git checkout -b feature/add-payment-integration

# Or create branch without switching
git branch feature/add-payment-integration
```

### Step 4: Verify Your New Branch
**Using VSCode:**
- Check the bottom-left corner shows your new branch name

**Using Terminal:**
```bash
git branch
# The current branch will have an asterisk (*)
```

---

## Making Changes and Commits

### Step 1: Make Your Code Changes
Edit your files as needed in VSCode.

### Step 2: Review Changes
**Using VSCode:**
1. Open Source Control panel (`Ctrl+Shift+G`)
2. You'll see all modified files listed
3. Click on a file to see the diff (changes highlighted)

**Using Terminal:**
```bash
# See what files have changed
git status

# View detailed changes
git diff
```

### Step 3: Stage Changes
You can stage all changes or select specific files.

**Using VSCode:**
- **Stage All:** Click the "+" icon next to "Changes"
- **Stage Individual Files:** Click "+" icon next to each file

**Using Terminal:**
```bash
# Stage all changes
git add .

# Stage specific file
git add path/to/file.js

# Stage multiple specific files
git add file1.js file2.js file3.js
```

### Step 4: Commit Changes
Write clear, descriptive commit messages!

**Good Commit Messages:**
```
✓ Add user authentication feature
✓ Fix login validation error
✓ Refactor API endpoint structure
✓ Update dependencies to latest versions
```

**Poor Commit Messages:**
```
✗ Fix
✗ Updates
✗ Changes
✗ asdf
```

**Using VSCode:**
1. Type your commit message in the message box at the top of Source Control panel
2. Press `Ctrl+Enter` (or `Cmd+Enter`) to commit
3. Or click the checkmark icon

**Using Terminal:**
```bash
# Commit with message
git commit -m "Add user authentication feature"

# Commit with detailed message
git commit -m "Add user authentication feature" -m "- Implement JWT token generation
- Add login/logout endpoints
- Create authentication middleware"
```

### Best Practice: Commit Frequently
- Commit logical units of work
- Don't wait until end of day to commit everything
- Each commit should represent a complete, working change
- Smaller commits are easier to review and revert if needed

---

## Pushing Your Branch to ADO

### First-Time Push (Set Upstream)
When pushing a new branch for the first time:

**Using VSCode:**
1. Click "..." in Source Control panel
2. Select **Push**
3. VSCode will prompt to set upstream - click **OK**

**Using Terminal:**
```bash
# Push and set upstream tracking
git push -u origin feature/add-payment-integration
```

### Subsequent Pushes
After the first push, simply:

**Using VSCode:**
1. Click the sync icon (circular arrows) at the bottom-left
2. Or click "..." → **Push**

**Using Terminal:**
```bash
git push
```

### Verify Push Success
**Using Terminal:**
```bash
git status
# Should show: Your branch is up to date with 'origin/feature-name'
```

---

## Creating a Pull Request in Azure DevOps

### Step 1: Navigate to Azure DevOps
1. Open your browser
2. Go to your Azure DevOps organization URL: `https://dev.azure.com/{your-org}/{your-project}`
3. Click on **Repos** → **Pull Requests**

### Step 2: Create New Pull Request
1. Click **New Pull Request** button (top-right)
2. **Alternative:** After pushing, ADO often shows a banner: "Create a pull request for {your-branch}" - click that

### Step 3: Configure Pull Request Details

#### Source and Target Branches
- **Source branch:** Your feature branch (e.g., `feature/add-payment-integration`)
- **Target branch:** Usually `main` (or `develop` depending on your workflow)

#### Title
Write a clear, descriptive title:
```
✓ Add payment integration with Stripe
✓ Fix critical bug in user authentication
✓ Refactor database connection logic
```

#### Description
Provide context for reviewers:

**Template Example:**
```markdown
## Summary
Brief description of what this PR does

## Changes Made
- Added payment processing module
- Integrated Stripe API
- Created payment confirmation page
- Updated user profile to show payment history

## Testing Done
- Unit tests for payment processing
- Integration tests with Stripe sandbox
- Manual testing of payment flow

## Related Work Items
- Fixes #1234
- Related to #5678

## Screenshots (if applicable)
[Attach screenshots]

## Checklist
- [ ] Code builds without errors
- [ ] Tests pass
- [ ] Documentation updated
- [ ] No merge conflicts
```

### Step 4: Set Reviewers
1. Click **Reviewers** section
2. Add team members who should review your code
3. Set as **Required** or **Optional** reviewers

### Step 5: Link Work Items
1. Click **Related Work Items**
2. Link associated user stories, bugs, or tasks
3. This helps track which code changes relate to which requirements

### Step 6: Set Policies (if available)
- **Auto-complete:** PR merges automatically after all approvals
- **Delete source branch:** Cleans up after merge
- **Squash merge:** Combines all commits into one

### Step 7: Create Pull Request
Click **Create** button

### Step 8: Review Process
1. Wait for reviewers to provide feedback
2. Address comments (see scenarios below)
3. Request re-review if needed
4. Once approved, merge the PR

---

## Common Scenarios

### Scenario 1: Adding New Changes to an Open PR

You have an open PR, but need to add more changes based on feedback or forgotten work.

**Steps:**
1. **Ensure you're on the correct branch:**
   ```bash
   git checkout feature/add-payment-integration
   ```

2. **Make your additional changes** in VSCode

3. **Stage and commit the new changes:**
   ```bash
   git add .
   git commit -m "Address review feedback: Add error handling"
   ```

4. **Push to the same branch:**
   ```bash
   git push
   ```

5. **Result:** The PR in ADO automatically updates with your new commits!

**Important Notes:**
- The PR doesn't need to be recreated
- All new commits appear in the PR
- Reviewers are notified of updates
- Previous comments remain visible

---

### Scenario 2: Syncing Your Branch with Updated Main

Main branch has been updated since you created your feature branch.

**Steps:**
1. **Commit or stash your current work:**
   ```bash
   # If you have uncommitted changes, stash them
   git stash

   # Or commit them
   git add .
   git commit -m "Work in progress"
   ```

2. **Switch to main and pull latest:**
   ```bash
   git checkout main
   git pull origin main
   ```

3. **Switch back to your feature branch:**
   ```bash
   git checkout feature/add-payment-integration
   ```

4. **Rebase or merge main into your branch:**

   **Option A - Rebase (cleaner history):**
   ```bash
   git rebase main
   ```

   **Option B - Merge (preserves history):**
   ```bash
   git merge main
   ```

5. **Resolve any conflicts** (see Scenario 4)

6. **If you stashed, restore your changes:**
   ```bash
   git stash pop
   ```

7. **Push your updated branch:**
   ```bash
   # If you rebased, you'll need force push
   git push --force-with-lease

   # If you merged, normal push works
   git push
   ```

**Best Practice:** Prefer `--force-with-lease` over `--force` as it's safer.

---

### Scenario 3: Resolving Merge Conflicts

Conflicts occur when the same lines of code are modified in both branches.

**Using VSCode (Recommended):**
1. When conflicts occur, VSCode highlights them automatically
2. Click on the conflicted file in Source Control panel
3. You'll see conflict markers with options:
   - **Accept Current Change** (your changes)
   - **Accept Incoming Change** (changes from main)
   - **Accept Both Changes**
   - **Compare Changes** (side-by-side view)

4. Choose the appropriate option or manually edit
5. After resolving all conflicts:
   ```bash
   git add .
   git rebase --continue  # If you were rebasing
   # OR
   git commit              # If you were merging
   ```

**Using Terminal:**
1. Open conflicted files in VSCode
2. Look for conflict markers:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Changes from main
   >>>>>>> main
   ```
3. Edit the file to resolve conflicts
4. Remove conflict markers
5. Stage and complete the merge/rebase:
   ```bash
   git add .
   git rebase --continue  # or git commit
   ```

---

### Scenario 4: Undoing Uncommitted Changes

You made changes but want to discard them.

**Discard All Uncommitted Changes:**

**Using VSCode:**
1. Source Control panel → "..." → **Discard All Changes**
2. Confirm the action

**Using Terminal:**
```bash
git restore .
# Or older syntax: git checkout -- .
```

**Discard Changes in Specific File:**

**Using VSCode:**
- Right-click the file in Source Control → **Discard Changes**

**Using Terminal:**
```bash
git restore path/to/file.js
```

---

### Scenario 5: Amending the Last Commit

You committed but forgot to include a file or want to update the commit message.

**Using Terminal:**
```bash
# Make additional changes
git add forgotten-file.js

# Amend the last commit
git commit --amend

# Or amend with new message
git commit --amend -m "Updated commit message"

# If already pushed, you'll need force push
git push --force-with-lease
```

**Warning:** Only amend commits that haven't been pushed or shared with others!

---

### Scenario 6: Working with Multiple Feature Branches

You need to switch between different features.

**Steps:**
1. **Commit or stash current work:**
   ```bash
   git stash save "WIP: Payment integration"
   ```

2. **Switch to another branch:**
   ```bash
   git checkout feature/other-feature
   ```

3. **Do your work on the other branch**

4. **Switch back and restore:**
   ```bash
   git checkout feature/add-payment-integration
   git stash pop
   ```

**View all stashes:**
```bash
git stash list
```

**Apply specific stash:**
```bash
git stash apply stash@{0}
```

---

### Scenario 7: Reviewing Someone Else's PR

**In Azure DevOps:**
1. Go to **Repos** → **Pull Requests**
2. Click on the PR to review
3. Click on **Files** tab to see changes
4. Add comments by clicking on specific lines
5. Use **Overview** tab to see overall discussion

**To Test Locally:**
```bash
# Fetch all branches
git fetch origin

# Checkout the PR branch
git checkout feature/their-feature-branch

# Pull latest changes
git pull

# Run/test the code locally
```

---

### Scenario 8: Squashing Commits Before Merge

You have many small commits and want to combine them into one.

**Interactive Rebase:**
```bash
# Squash last 5 commits
git rebase -i HEAD~5
```

This opens an editor:
```
pick abc123 First commit
pick def456 Second commit
pick ghi789 Third commit
pick jkl012 Fourth commit
pick mno345 Fifth commit
```

Change to:
```
pick abc123 First commit
squash def456 Second commit
squash ghi789 Third commit
squash jkl012 Fourth commit
squash mno345 Fifth commit
```

Save and close. Git will combine all commits into one.

```bash
# Force push the squashed commits
git push --force-with-lease
```

**Note:** ADO also offers "Squash merge" option when merging a PR, which is easier!

---

### Scenario 9: Cherry-Picking Specific Commits

You want to apply a specific commit from one branch to another.

**Steps:**
```bash
# Find the commit hash you want to cherry-pick
git log --oneline

# Switch to target branch
git checkout main

# Cherry-pick the commit
git cherry-pick abc123def

# Push if needed
git push
```

---

### Scenario 10: Deleting Branches After PR Merge

**Delete Local Branch:**
```bash
# Switch to main first
git checkout main

# Delete the feature branch
git branch -d feature/add-payment-integration

# Force delete if needed
git branch -D feature/add-payment-integration
```

**Delete Remote Branch:**
```bash
git push origin --delete feature/add-payment-integration
```

**Using VSCode:**
1. Click on branch name (bottom-left)
2. Right-click on the branch you want to delete
3. Select **Delete Branch**

**Note:** ADO can automatically delete the source branch after PR merge (enable this option when creating PR).

---

## Best Practices

### 1. Commit Message Conventions

Follow a consistent format:
```
<type>: <short summary>

<optional detailed description>

<optional footer>
```

**Types:**
- `feat:` New feature
- `fix:` Bug fix
- `refactor:` Code refactoring
- `docs:` Documentation changes
- `test:` Adding/updating tests
- `chore:` Maintenance tasks
- `style:` Code style changes (formatting)

**Examples:**
```
feat: Add user authentication with JWT

- Implement login/logout endpoints
- Create authentication middleware
- Add token refresh mechanism

Closes #123
```

### 2. Branch Management

**Branch Naming:**
- Use lowercase with hyphens
- Include type and description
- Examples: `feature/user-auth`, `bugfix/login-error`, `hotfix/critical-security`

**Keep Branches Short-Lived:**
- Merge within 1-3 days if possible
- Avoid long-living feature branches
- Regularly sync with main

**Branch Protection:**
- Enable branch policies in ADO for main/develop
- Require PR reviews before merge
- Require build validation

### 3. Pull Request Best Practices

**Keep PRs Small:**
- Aim for 200-400 lines of code changes
- One feature/fix per PR
- Easier to review and test

**Write Good Descriptions:**
- Explain the "why" not just the "what"
- Include testing steps
- Link related work items

**Request the Right Reviewers:**
- Include code owners
- Include someone familiar with the area
- Minimum 1-2 reviewers

**Respond to Feedback:**
- Address all comments
- Explain decisions if you disagree
- Be respectful and professional

### 4. Code Review Etiquette

**As a Reviewer:**
- Be constructive and respectful
- Explain the reasoning behind suggestions
- Approve promptly if changes look good
- Use questions instead of demands: "Could we...?" vs "You must..."

**As an Author:**
- Don't take feedback personally
- Ask for clarification if needed
- Thank reviewers for their time
- Fix issues promptly

### 5. Keep Your Local Repository Clean

**Regularly Prune:**
```bash
# Remove local branches that are deleted remotely
git fetch --prune

# Clean up stale references
git remote prune origin
```

**Fetch Updates Regularly:**
```bash
# Update all remote branches
git fetch --all
```

### 6. Use .gitignore Properly

Ensure these are never committed:
- `node_modules/`
- `.env` files
- IDE-specific files (`.vscode/`, `.idea/`)
- Build outputs (`dist/`, `build/`)
- Log files
- OS files (`.DS_Store`, `Thumbs.db`)

### 7. Protect Sensitive Data

**Never Commit:**
- Passwords
- API keys
- Access tokens
- Private keys
- Database connection strings

**If Accidentally Committed:**
```bash
# Remove from history (requires force push!)
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch path/to/sensitive/file" \
  --prune-empty --tag-name-filter cat -- --all

# Then force push
git push --force --all
```

**Better:** Use environment variables and `.env` files (gitignored).

### 8. Testing Before Pushing

**Pre-Push Checklist:**
- [ ] Code builds successfully
- [ ] All tests pass
- [ ] No linting errors
- [ ] No console.log() or debugging code left
- [ ] Updated documentation if needed

**Run Tests:**
```bash
# Run unit tests
npm test

# Run linter
npm run lint

# Build project
npm run build
```

### 9. Use Git Hooks

**Pre-commit Hook Example:**
Create `.git/hooks/pre-commit`:
```bash
#!/bin/sh
npm run lint
npm test
```

Make it executable:
```bash
chmod +x .git/hooks/pre-commit
```

**Tools:** Use Husky for easier hook management.

### 10. Document Your Workflow

Maintain a `CONTRIBUTING.md` file in your repository with:
- Branch naming conventions
- Commit message format
- PR process
- Code review guidelines
- Testing requirements

---

## Troubleshooting

### Issue: "Fatal: Not a git repository"

**Solution:**
```bash
git init
```

### Issue: "Permission denied (publickey)"

**Solution:** Set up SSH keys or use HTTPS.

**Check remote URL:**
```bash
git remote -v
```

**Switch to HTTPS:**
```bash
git remote set-url origin https://dev.azure.com/{org}/{project}/_git/{repo}
```

### Issue: "Merge conflicts" causing confusion

**Solution:**
1. Don't panic!
2. Use VSCode's visual merge conflict resolver
3. Test after resolving
4. Ask for help if unsure

### Issue: "Detached HEAD state"

**Solution:**
```bash
# Create a branch from current state
git branch temp-branch

# Switch to the branch
git checkout temp-branch
```

### Issue: "Your branch and 'origin/branch' have diverged"

**Solution:**
```bash
# Pull with rebase
git pull --rebase origin your-branch

# Or if you want to keep remote version
git reset --hard origin/your-branch
```

### Issue: Accidentally Committed to Main

**Solution:**
```bash
# Don't panic! Create a branch with your changes
git branch feature/my-changes

# Reset main to remote state
git reset --hard origin/main

# Switch to your new branch
git checkout feature/my-changes
```

### Issue: Need to Undo Last Commit

**Keep Changes:**
```bash
git reset --soft HEAD~1
```

**Discard Changes:**
```bash
git reset --hard HEAD~1
```

### Issue: Lost Commits After Reset

**Solution:** Git keeps everything for ~30 days!
```bash
# Find lost commits
git reflog

# Restore to specific commit
git reset --hard abc123def
```

---

## Quick Reference Commands

### Basic Commands
```bash
# Check status
git status

# View history
git log --oneline --graph --all

# Create branch
git checkout -b branch-name

# Switch branch
git checkout branch-name

# Pull latest
git pull origin main

# Push changes
git push -u origin branch-name

# View remotes
git remote -v

# Fetch all branches
git fetch --all
```

### Undoing Changes
```bash
# Discard uncommitted changes
git restore file.js

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert a commit (create new commit that undoes it)
git revert abc123def
```

### Branch Management
```bash
# List all branches
git branch -a

# Delete local branch
git branch -d branch-name

# Delete remote branch
git push origin --delete branch-name

# Rename current branch
git branch -m new-name
```

### Stashing
```bash
# Stash changes
git stash

# Stash with message
git stash save "WIP: feature work"

# List stashes
git stash list

# Apply latest stash
git stash pop

# Apply specific stash
git stash apply stash@{0}

# Drop stash
git stash drop stash@{0}
```

---

## VSCode Keyboard Shortcuts

### Windows/Linux
- `Ctrl+Shift+G` - Open Source Control
- `Ctrl+K Ctrl+O` - Open folder
- `Ctrl+Shift+P` - Command Palette
- `Ctrl+Enter` - Commit staged changes
- `Ctrl+Shift+F` - Search across files

### Mac
- `Cmd+Shift+G` - Open Source Control
- `Cmd+K Cmd+O` - Open folder
- `Cmd+Shift+P` - Command Palette
- `Cmd+Enter` - Commit staged changes
- `Cmd+Shift+F` - Search across files

---

## Additional Resources

### Official Documentation
- [Git Documentation](https://git-scm.com/doc)
- [Azure DevOps Documentation](https://docs.microsoft.com/en-us/azure/devops/)
- [VSCode Git Integration](https://code.visualstudio.com/docs/sourcecontrol/overview)

### Learning Resources
- [Pro Git Book](https://git-scm.com/book/en/v2) (Free)
- [Learn Git Branching](https://learngitbranching.js.org/) (Interactive)
- [Oh My Git!](https://ohmygit.org/) (Game-based learning)

### Tools
- **GitLens** - Advanced Git features in VSCode
- **Git Graph** - Visualize repository history
- **Azure Repos Extension** - Enhanced ADO integration

---

## Conclusion

Mastering Git and VSCode integration takes practice, but following these best practices will help you:
- Work more efficiently
- Collaborate better with your team
- Maintain a clean, understandable Git history
- Resolve issues quickly when they arise

**Remember:**
- Commit often, push regularly
- Write clear commit messages
- Keep PRs small and focused
- Communicate with your team
- Don't be afraid to ask for help!

Happy coding! 🚀

---

**Document Version:** 1.0
**Last Updated:** 2025-11-17
**Maintained By:** Development Team
