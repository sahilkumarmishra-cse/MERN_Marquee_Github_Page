# MERN Marquee — Git & GitHub Guide

This README provides a compact introduction to Git, GitHub, Git Bash, and GitHub Pages, lists important Git commands, explains why Git matters in industry, and documents how to deploy this project to GitHub Pages.

## What is Git?

Git is a distributed version control system that tracks changes to files and helps multiple developers collaborate on a codebase. Key features:

- Local commits and history: record changes locally before sharing.
- Branching and merging: isolate features and integrate safely.
- Distributed model: every clone is a full repository.

## What is GitHub?

GitHub is a cloud platform that hosts Git repositories, provides collaboration features (pull requests, issues, code review), and offers CI/CD and Pages hosting. It makes sharing and maintaining projects easier for teams and open-source communities.

## What is Git Bash?

Git Bash is a command-line environment for Windows that provides Git command-line features and a Bash shell. Use it to run Git commands, basic shell scripting, and common CLI tools on Windows.

## What is GitHub Pages?

GitHub Pages is a static site hosting service from GitHub. It serves static content (HTML/CSS/JS) directly from a repository branch (commonly `main` or `gh-pages`) or from a `/docs` folder. It's ideal for project sites, documentation, and simple portfolios.

## Important Git Commands (cheat sheet)

Basic repository lifecycle:

```
git init                # initialize a new repo
git clone <url>         # clone a remote repo
git status              # show working tree status
git add <file|.>        # stage changes
git commit -m "msg"    # commit staged changes
git push                # push commits to remote
git pull                # fetch + merge from remote
```

Branching and merging:

```
git branch              # list branches
git branch <name>       # create branch
git checkout <name>     # switch branch
git checkout -b <name>  # create and switch
git merge <branch>      # merge branch into current
```

Inspecting history and changes:

```
git log                 # view commit history
git diff                # show unstaged changes
git show <commit>       # show a commit
```

Undoing changes:

```
git restore <file>           # discard working-tree changes
git reset --soft <commit>    # move HEAD, keep index
git reset --hard <commit>    # reset working tree (CAUTION)
```

Working with remotes:

```
git remote -v         # show remotes
git remote add origin <url>
git push -u origin main
```

## Why Git Matters in Industry

- Collaboration: Facilitates teamwork via branching, PRs, and code reviews.
- Traceability: Every change is recorded with an author, timestamp, and message.
- Reliability: Roll back or isolate changes easily if bugs appear.
- Automation: Integrates with CI/CD pipelines for testing and deployment.
- Standardization: Most companies expect Git fluency during hiring and day-to-day work.

## Deploying This Project to GitHub Pages

This project contains a simple static site (index.html + style.css). Use one of the methods below to publish it.

Option A — Quick (recommended for this repo)

1. Commit and push your code to the `main` (or `master`) branch.
2. On GitHub, open the repository > Settings > Pages.
3. Under "Build and deployment" / "Source", select `main` branch and `/ (root)` (or `/docs` if you keep files there).
4. Save. GitHub will provide a URL (e.g., `https://<username>.github.io/<repo>/`).

Option B — Use `gh-pages` branch (common for static site workflows)

1. Install the `gh-pages` tool (if using npm projects):

```bash
npm install --save-dev gh-pages
```

2. Add deploy scripts to `package.json` (for Node-based projects):

```json
"scripts": {
	"predeploy": "npm run build",
	"deploy": "gh-pages -d build"
}
```

3. Run `npm run deploy` to publish to the `gh-pages` branch.

Option C — Use GitHub Actions (automated CI/CD)

- Create a workflow that builds and pushes site files to the Pages branch automatically on push to `main`.

Manual push commands (example)

```bash
git add .
git commit -m "Publish site"
git push origin main
```

After pushing, wait a minute and visit the Pages URL shown in the repository settings.

## Notes & Best Practices

- Write clear commit messages and small commits.
- Use branches for features/bugfixes and open pull requests for reviews.
- Protect the `main` branch with required reviews and CI checks in team projects.
- Keep secrets out of the repo (use Actions secrets or environment variables).

---
