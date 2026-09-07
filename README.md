# Firstrepo
# Git and GitHub: Next Steps

*Part 2 — Branching, Pull Requests, and Collaborative Documentation*
*TechCrush Technical Writing Bootcamp*

---

## Recap

In Part 1, you learned to install Git, create a GitHub account, and push your first commit. Now we'll build the skills you need to **collaborate** on documentation the way real writing teams do.

---

## Part 1: Branching

### Why branch?

A branch is an independent line of work. Instead of editing the main version of a document directly, you create a branch, make your changes there, and merge them back once they're ready. This keeps the main copy stable while you experiment or draft.

Think of it like working on a **copy of a document** before replacing the original — except Git tracks exactly what changed and lets you combine work automatically.

### Creating and switching branches

```
git branch new-section
git checkout new-section
```

Or do both in one step:

```
git checkout -b new-section
```

### Checking which branch you're on

```
git branch
```

The branch with an asterisk (`*`) is your current one.

### Making changes and committing on a branch

```
git add .
git commit -m "Draft new troubleshooting section"
git push -u origin new-section
```

The `-u origin new-section` tells Git to create this branch on GitHub too, and remember the connection for future pushes.

---

## Part 2: Merging

### Merging locally

Once your branch is ready, switch back to `main` and merge:

```
git checkout main
git merge new-section
```

### Merging on GitHub (the more common approach)

Most teams merge through GitHub itself using a **Pull Request** (covered next), rather than merging locally. This creates a record of the change and allows others to review it first.

---

## Part 3: Pull Requests (PRs)

A **Pull Request** is a request to merge your branch into another branch (usually `main`). It's the heart of collaborative work on GitHub.

### Opening a Pull Request

1. Push your branch to GitHub (as shown above)
2. Go to your repository on GitHub — you'll see a prompt: *"Compare & pull request"*
3. Click it, add a clear title and description of what you changed and why
4. Click **Create pull request**

### What makes a good PR description (for technical writers)

- **What changed:** e.g., "Added a troubleshooting section to the installation guide"
- **Why:** e.g., "Users were getting stuck on step 3 with no guidance"
- **How to review:** e.g., "Check that terminology matches the glossary"

### Reviewing a Pull Request

Reviewers can:
- Leave comments on specific lines
- Request changes
- Approve the PR

Once approved, the PR is merged into `main` — usually by clicking **Merge pull request** on GitHub.

---

## Part 4: Handling Conflicts

Sometimes two people edit the same lines of a file. Git will flag this as a **merge conflict** and ask you to resolve it manually.

A conflict looks like this inside the file:

```
<<<<<<< HEAD
This is the original wording.
=======
This is the new wording from the branch.
>>>>>>> new-section
```

To resolve it:
1. Decide which version (or combination) to keep
2. Delete the `<<<<<<<`, `=======`, and `>>>>>>>` markers
3. Save, then commit:

```
git add .
git commit -m "Resolve merge conflict in installation guide"
```

---

## Part 5: Writing Documentation Directly in Markdown

GitHub renders `.md` files automatically, making Markdown the standard format for docs-as-code. A few conventions to know:

| Markdown | Renders as |
|---|---|
| `# Heading` | Large heading |
| `**bold**` | **bold** |
| `` `code` `` | `code` |
| `- item` | Bullet list |
| `[text](url)` | Hyperlink |
| ` ```code block``` ` | Formatted code block |

### Editing directly on GitHub

For small edits, you don't need your laptop at all:
1. Open the `.md` file in your repository
2. Click the pencil (✏️) icon to edit
3. Make your change
4. Scroll down, add a commit message, and choose **"Create a new branch and start a pull request"**

This is a common workflow for reviewing and suggesting documentation fixes without touching the command line.

---

## Part 6: Collaborating on a Shared Documentation Project

A typical team workflow looks like this:

1. **Clone** the shared repository
2. **Pull** the latest changes before starting work: `git pull`
3. Create a **branch** for your task
4. Make edits and **commit** regularly with clear messages
5. **Push** your branch and open a **Pull Request**
6. Respond to review comments, make follow-up commits if needed
7. Once approved, the PR is **merged**

### Good commit message habits

- Use the present tense: "Add," not "Added"
- Be specific: "Fix broken link in Chapter 3" rather than "Fix stuff"
- Keep the first line under 50 characters where possible

---

## Quick Reference: Collaboration Commands

| Command | What it does |
|---|---|
| `git checkout -b <branch>` | Create and switch to a new branch |
| `git push -u origin <branch>` | Push a new branch to GitHub |
| `git pull` | Update your local copy with the latest changes |
| `git merge <branch>` | Merge a branch into your current branch |
| `git log --oneline` | View a compact commit history |

---

## Practice Exercise

1. Create a new branch called `practice-edit`
2. Add a new section to `notes.md` from Part 1
3. Commit and push the branch
4. Open a Pull Request on GitHub describing your change
5. Merge it once you've reviewed your own PR

*Bring any questions or errors you encounter to our next session — troubleshooting real issues is part of the learning process.*
