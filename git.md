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

## 9. Local Repository vs. Remote Repository

### Local repository

- Exists on your computer or server.
- Stores local commits and repository history.
- Allows you to create branches and inspect history without a network connection.

### Remote repository

- Is another repository, often hosted on GitLab or GitHub.
- Lets developers exchange commits and collaborate.
- Is accessed through a remote name and URL, commonly `origin`.

Examples:
