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
   - Uses a central server to store the shared version history.
   - Developers check out files and submit changes to the central server.
   - Collaboration generally depends on access to that server.
   - Example: traditional Subversion (SVN) workflows.

<img width="832" height="358" alt="Screenshot 2026-10-26 at 8 13 48 PM" src="https://github.com/user-attachments/assets/55380cd1-1637-4d18-965b-fac665fb1225" />


2. **DVCS — Distributed Version Control System**
   - Each clone normally contains the repository history, not just a working copy of files.
   - Developers can commit changes locally and work without a continuous connection to the remote server.
   - Changes can later be shared with other repositories.
   - Example: Git.
