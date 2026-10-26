## 1. What Is Source Code Management?

Source Code Management (SCM) is the practice of tracking and managing changes to source code and other project files over time.

- It records who changed files and when.
- It helps developers collaborate on the same project.
- It makes it possible to review differences between versions.
- It helps teams recover previous versions when necessary.
- It supports controlled software development and release workflows.

## 2. What Is Version Control?

A Version Control System (VCS) records changes to files so that earlier versions can be inspected or recovered.

1. **CVCS — Centralized Version Control System**
   - A central server is one main computer that stores the project's files and records all the changes made to them over time.
   - Developers download the project files from the main server, make changes on their computers, and send those changes back to the server.
   - Collaboration generally depends on access to that server.
   - Example: traditional Subversion (SVN) workflows.

<img width="832" height="358" alt="Screenshot 2026-10-26 at 8 13 48 PM" src="https://github.com/user-attachments/assets/55380cd1-1637-4d18-965b-fac665fb1225" />


2. **DVCS — Distributed Version Control System**
   - Each clone normally contains the repository history, not just a working copy of files.
   - Developers can commit changes locally and work without a continuous connection to the remote server.
   - Changes can later be shared with other repositories.
   - Example: Git.
<img width="907" height="510" alt="Screenshot 2026-10-26 at 8 20 55 PM" src="https://github.com/user-attachments/assets/d9e558c2-e505-4ba8-9bfe-87216da2ab12" />


## 3. Repository

A **repository** is where Git stores project history and the metadata it needs to track changes.

- **Local repository:** The repository on your computer or server.
- **Remote repository:** Another repository used to exchange changes, often hosted on GitLab or GitHub.
- A repository contains commit history, branches, tags, and Git metadata.

## 4. Workspace / Working Directory / Working Tree
All three terms generally refer to the place where you work on your project files.
Example: You have a project folder containing app.js. When you open and edit app.js, you are working in your working directory or working tree.
- Workspace: The place where you work on your project.
- Working directory: The folder containing your project files.
- Working tree: The files you can see and modify in your Git project.

## 5. Commit / Check-in

A **commit** records a snapshot of the staged project state in the local repository.

- A commit includes metadata such as author, message, timestamp, and parent commit references.
- The commit message should briefly explain the change.
- A commit does not automatically upload the change to a remote repository.

## 5. Version / Version ID / Commit ID

- **Version:** An informal term for a particular state or release of a project.
- **Commit ID:** The identifier for a particular Git commit.
- **Version ID:** A general phrase that may mean a commit ID, tag, or release identifier, depending on the context.

View commit IDs:

```bash
git log --oneline
git rev-parse HEAD
```

## 6. Advantages of Git

1. **Change history:** Inspect previous commits and changes.
2. **Branching:** Work on separate features and fixes.
3. **Collaboration:** Exchange changes with other developers.
4. **Offline work:** Commit locally without always connecting to a server.
5. **Comparison:** Review differences between versions.
6. **Recovery:** Restore earlier states or reverse changes.
7. **Code review:** Use branches and hosting platforms to propose changes.
8. **CI/CD integration:** Connect repositories to automated build and deployment pipelines.
9. **Distributed design:** Each clone normally has its own repository history.


## 7. Git Snapshots

A **snapshot** represents the project state recorded by a commit.

- A commit records the state of the files tracked by Git at that point.
- Commits are connected through parent references to form history.
- Git can reuse unchanged file content internally instead of storing a completely separate full copy for every commit.
- Snapshots make it possible to compare and inspect earlier project states.

Example:

```bash
git log --oneline
git show <commit-id>
```
## 8. Staging Area

The **staging area**, also called the **index**, holds the changes selected for the next commit.

- The working tree contains the files you edit.
- `git add` stages selected changes.
- `git commit` records the staged state.

Example:

```bash
echo "Staging example" > staging.txt
git status
git add staging.txt
git status
git commit -m "Add staging example"
```

## 9. Local Repository vs. Remote Repository

### Local repository

- Exists on your computer or server.
- Stores local commits and repository history.
- Allows you to create branches and inspect history without a network connection.

### Remote repository

- Is another repository, often hosted on GitLab or GitHub.
- Lets developers exchange commits and collaborate.
- Is accessed through a remote name and URL, commonly `origin`.


## 10. Git Installation and Configuration

### Install on Ubuntu / Debian

```bash
sudo apt update
sudo apt install git -y
git --version
```

## 11. `git add`

Stages selected changes so they can be included in the next commit.

```bash
git add README.md
git add .
```

- `git add README.md` stages changes to the named file.
- `git add .` stages changes under the current directory within the repository.
- Check the staged changes with `git status` before committing.

## 12. `git commit`

Records the staged changes as a commit in the local repository.

```bash
git commit -m "Add project README"
```

- Use a short, meaningful commit message.
- Only staged changes are included in the commit.
- A commit does not automatically push changes to a remote repository.

## 13. `git log`

Displays the repository's commit history.

```bash
git log
git log --oneline
git log --graph --oneline --all
```

- `git log` shows detailed commit information.
- `git log --oneline` displays a compact history.
- `git log --graph --oneline --all` helps visualize branch history.

## 14. `git push`

Sends local commits to a remote repository.

```bash
git push origin main
git push -u origin feature-login
```

- `origin` is a common remote name.
- `main` is the branch being pushed in the first example.
- `-u` sets the upstream for a new branch, making future pushes easier.
- The remote URL and authentication must be configured correctly.

## 15. `git status`

Shows the current branch and the state of files.

```bash
git status
git status --short
```

Git can report files as:

- **Untracked:** Git is not tracking the file yet.
- **Modified:** A tracked file has changed.
- **Staged:** Changes are selected for the next commit.
- **Clean:** No pending changes are reported.


## 16. `.gitignore`

`.gitignore` is a file containing patterns for files and directories that Git should intentionally leave untracked.

Example `.gitignore`:

```gitignore
.env
node_modules/
*.log
dist/
```

## 17. `git branch`

Lists, creates, or manages branches.

```bash
git branch
git branch feature-login
git branch -a
```

- `git branch` lists local branches.
- `git branch feature-login` creates a branch.
- `git branch -a` lists local and remote-tracking branches.

Create and switch to a branch:

```bash
git switch -c feature-login
```

## 18. `git checkout`

Can switch branches or check out a particular commit or file state.

```bash
git checkout main
git checkout -b feature-login
```

- `git checkout main` switches to `main`.
- `git checkout -b feature-login` creates and switches to a new branch.
- Modern Git also provides `git switch` for branch switching and `git restore` for restoring files.


## 19. `git merge`

Integrates changes from another branch into the current branch.

```bash
git switch main
git merge feature-login
```

- The current branch is the branch receiving the changes.
- Git may perform a fast-forward merge or create a merge commit.
- A merge may require conflict resolution.




