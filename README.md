## Common Git "Undo" & Edit Scenarios

### Table of Contents
- [Situation 1: Undo Commit & Staging](#situation-1-undo-commit--staging-everything-back-to-untracked)
- [Situation 2: Undo Commit, Keep Changes Staged](#situation-2-undo-commit-keep-changes-staged-edit-before-recommitting)
- [Situation 3: Edit a Pushed Commit Without Creating a New One](#situation-3-edit-a-pushed-commit-without-creating-a-new-one)
- [Situation 4: Delete a Branch](#situation-4-delete-a-branch)
- [Situation 5: View Branches](#situation-5-view-branches)

---

### **Situation 1: Undo Commit & Staging (everything back to untracked)**

> You committed changes locally (not pushed yet) and want to go back as if you never staged or committed anything.

```bash
git reset HEAD~1
```
- This completely undoes your last commit and unstages all files, returning them to their previous state (changes are kept as unstaged modifications).

---

### **Situation 2: Undo Commit, Keep Changes Staged (edit before recommitting)**

> You committed and staged changes (not pushed), but want to modify what's staged (add/remove/unstage files) before recommitting.

```bash
git reset --soft HEAD~1
```
- This removes the last commit but keeps all files staged.
- To unstage a file (remove from the staging area):
  ```bash
  git restore --staged <file-name>
  ```

---

### **Situation 3: Edit a Pushed Commit Without Creating a New One**

> You already pushed a commit but later realize you need to add/remove/edit files in that same commit (not create a new one).

1. Stage your changes:
    ```bash
    git add .
    ```
2. Amend the previous commit:
    - To just update files, keeping the old message:
      ```bash
      git commit --amend --no-edit
      ```
    - To edit the commit message:
      ```bash
      git commit --amend -m "new message"
      ```
3. Force-update the remote branch:
    ```bash
    git push --force-with-lease
    ```

*Note: Amending pushed commits rewrites history and should be used with care when collaborating with others.*

---

### **Situation 4: Delete a Branch**

> You want to remove a branch that you no longer need, either locally or from the remote repository.

#### Delete Branch Locally:
```bash
git branch -D branch-name
```
- This deletes the branch from your local repository.
- Use `-D` to force delete if the branch hasn't been fully merged.

#### Delete Branch from Remote (GitHub):
```bash
git push origin --delete branch-name
```
- This removes the branch from the remote repository on GitHub.

---

### **Situation 5: View Branches**

> Check what branches exist in your local repository and remote.

#### Local Branches:
```bash
git branch
```
- Lists all branches in your local repository.

#### Remote Branches:
```bash
git branch -r
```
- Lists all branches on the remote repository.

---
