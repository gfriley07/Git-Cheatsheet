# Git & GitHub Cheat Sheet

A quick-reference guide to installing Git, configuring your environment, and using common Git/GitHub commands.

---

## 1. Installation

| **Operating System** | **Steps**                                                                                                                     | **Commands/Links**                                                                                      |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Windows**          | 1. Download **Git for Windows** from the official website. <br>2. Run the installer.                                         | [Git for Windows](https://git-scm.com/download/win)                                                      |
| **macOS**            | 1. **Recommended:** Install Homebrew (if not installed). <br>2. Run `brew install git`. <br>**Alternate:** `xcode-select --install` | [Homebrew](https://brew.sh)                                                                              |
| **Linux (Ubuntu)**   | Update your package list, then install git.                                                                                  | <br>```bash<br>sudo apt update<br>sudo apt install git<br>```                                            |
| **Verify**           | Confirm Git is installed and check its version.                                                                              | <br>```bash<br>git --version<br>```                                                                      |

---

## 2. Setup & Configuration

| **Command**                                                            | **Description**                                           | **Example / Notes**                                                                                                                                     |
|------------------------------------------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `git config --global user.name "Your Name"`                            | Set your name (global)                                    | Use your real name or handle                                                                                                                            |
| `git config --global user.email "you@example.com"`                     | Set your email (global)                                   | Matches your GitHub account email                                                                                                                       |
| `git config --global init.defaultBranch main`                          | Default branch name to `main`                             | Instead of the older `master` name                                                                                                                      |
| `ssh-keygen -t ed25519 -C "you@example.com"`                           | Generate SSH key for GitHub                               | Copy the contents of `~/.ssh/id_ed25519.pub` to GitHub: **Settings > SSH and GPG Keys**                                                                 |
| `git config --list`                                                   | View all config settings                                  | Helpful for verifying your setup                                                                                                                        |

---

## 3. Basic Workflow

| **Command**              | **Description**                                                           | **Example / Notes**                                                                                     |
|--------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `git init`               | Initialize a new local Git repository                                     | Creates a `.git` folder in your current directory                                                       |
| `git clone <repo-url>`   | Clone a remote repository locally                                         | e.g., `git clone git@github.com:user/repo.git`                                                          |
| `git status`             | Check the state of your working directory and staging area               | Shows changed files, staged changes, untracked files, etc.                                              |
| `git add <file>`         | Stage individual file(s)                                                 | `git add .` stages **all** changes                                                                      |
| `git commit -m "message"`| Commit staged changes with a message                                     | Write clear, descriptive messages (e.g., “Add non-profit cloud Apex trigger”)                            |
| `git push origin <branch>`| Push local commits to the remote branch                                  | Usually `main` or `feature/my-feature`                                                                  |
| `git pull origin <branch>`| Fetch and merge remote changes into your local branch                   | Equivalent to `git fetch` + `git merge` for the same branch                                             |

---

## 4. Branching & Merging

| **Command**                               | **Description**                                                        | **Example / Notes**                                                                                        |
|-------------------------------------------|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `git branch`                              | List local branches                                                    | Add `-r` to list remote branches                                                                           |
| `git branch <new-branch>`                | Create a new branch (without switching to it)                          |                                                                                                            |
| `git checkout <branch>`                  | Switch to an existing branch                                          |                                                                                                            |
| `git checkout -b <new-branch>`           | Create and switch to a new branch at the same time                     | e.g., `git checkout -b feature/lwc-educ-cloud`                                                             |
| `git merge <branch>`                     | Merge another branch into the current branch                           | Switch to the target branch (e.g., `main`) before merging                                                  |
| `git rebase <branch>`                    | Rebase current branch on top of the specified branch                   | Creates a cleaner commit history, but **beware** rewriting history if you’ve pushed changes to a shared repo|

---

## 5. Remote Repositories & GitHub

| **Action**                          | **Description**                                                                             | **Example / Notes**                                                                                           |
|------------------------------------|---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| `git remote add origin <repo-url>` | Link a local repo to a remote (GitHub) repo                                                | e.g., `git remote add origin git@github.com:username/repo-name.git`                                            |
| `git push -u origin <branch>`      | Push a local branch to remote, setting it to track the upstream                            | The `-u` (or `--set-upstream`) flag associates local branch with the remote branch                             |
| **Create Pull Request**            | Push branch to GitHub, then open a Pull Request (PR) on GitHub’s website                   | Click “Compare & pull request” for the newly pushed branch                                                    |
| **Manage Issues**                  | Use GitHub Issues to track tasks or bugs                                                   | Reference issues in commits or PRs using `#<issue-number>`                                                    |
| **GitHub Pages**                   | Host static sites from a `gh-pages` branch (or the `docs/` folder in `main`)               | Configure in **Settings > Pages**                                                                             |

---

## 6. Troubleshooting

| **Command/Action**                              | **Description**                                                          | **Example / Notes**                                                                                                |
|-------------------------------------------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `git reset --soft HEAD~1`                       | Undo most recent commit but keep changes in staging                      | Leaves your changes so you can fix your commit message or add more changes                                          |
| `git reset --hard HEAD~1`                       | Discard the last commit **and** local changes                            | **Dangerous**: local changes will be lost                                                                           |
| `git stash`                                     | Temporarily save changes you don’t want to commit yet                    | Use `git stash pop` to re-apply stashed changes                                                                     |
| `git checkout -- <file>`                        | Discard local changes in a file (restore from HEAD)                      | **Dangerous**: This can’t be undone                                                                                 |
| **Fetch vs. Pull**                              | `git fetch` downloads remote changes, `git pull` merges them into local  |                                                                                                                      |
| **Merge Conflicts**                             | Occur when changes overlap across multiple commits/branches              | Resolve conflicts in the affected files, then `git add`, then commit                                               |

---

## 7. Tips & Best Practices

- **Commit Often & Meaningfully:** Helps track changes and revert easily if needed.  
- **Use Branches:** Keep `main` stable; develop in feature branches.  
- **Pull Requests & Code Reviews:** Encourage collaboration, catch bugs early, maintain code quality.  
- **Don’t Store Secrets in Git:** Use `.gitignore` or environment variables for sensitive info.  
- **Stay Organized:** Use tags (e.g., `v1.0.0`) for releases.

---

## 8. Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/en)
- [Pro Git eBook (Free)](https://git-scm.com/book/en/v2)
- [Git Cheat Sheet (GitHub)](https://training.github.com/) 
