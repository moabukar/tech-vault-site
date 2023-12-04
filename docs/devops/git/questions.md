<details>
<summary>What is Git?</summary>
  
Most widely used modern version control system in the world today. It is used to gather code contributions from multiple users in a single place (repository). Provides full history, workflow and allows for rollback of code and patching.
  
</details>
<br>

<details>
<summary>Difference between Git and SVN?</summary>
  
SVN and Git are both powerful version control systems that each use a different approach to managing and merging code changes. Git uses a distributed model, whereas SVN uses a centralized model.<br><br>

SVN’s centralized repository model makes it easier to manage contributions and contributors. Git does not support codebase access restrictions — a contributor who has access to the repository has access to the entire repository. SVN, by contrast, provides granular control, allowing for limits on particular contributors down to the directory, and file levels.<br><br>

The ability to work locally and offline is one major advantage to Git. SVN requires contributors to be connected to the main repository server, which essentially eliminates working offline.<br><br>

Git also outperforms SVN when it comes to merging and conflict resolution. Git has been designed for an open-source setting where numerous contributors may be working on the same parts of a codebase. To allow for this type of collaboration, Git has built up a robust system for resolving merge conflicts that makes the process smoother, and more manageable.

</details>
<br>

<details>
<summary>What is the basic Git workflow?</summary>

Working directory >   staging area >  local repo >   remote repo
            git add           git commit    git push 

</details>
<br>

<details>
  <summary>Difference between git pull and Git fetch</summary>
  
The key difference between git fetch and pull is that git pull copies changes from a remote repository directly into your working directory, while git fetch does not. The git fetch command only copies changes into your local Git repo. The git pull command does both.<br><br>

Benefit of git pull: The local Git repo is now in sync with the remote repo. The local filesystem has the latest, most up to date files.<br><br>

Benefit of git fetch: If you are actively working on files tracked by Git, but you still want to update your local repository with the latest changes from a remote repository, use the git fetch command.

</details>
<br>

<details>
<summary>What is git cherry-pick?</summary>

git cherry-pick is a Git command used to apply a specific commit (or a range of commits) from one branch to another. It allows you to select and "cherry-pick" individual commits from one branch's history and apply them onto another branch. This can be useful when you want to bring specific changes or fixes from one branch into another without merging the entire branch.<br><br>

The basic syntax of git cherry-pick is as follows:<br><br>

```bash

git cherry-pick <commit-hash>

<commit-hash> is the unique identifier (SHA-1 hash) of the commit you want to apply.

```

</details>
<br>

<details>
<summary>What is the HEAD in Git?</summary>


In Git, HEAD is a pointer to the latest commit in the currently checked-out branch. It represents the current state of the branch and is used for navigating the commit history and tracking changes. When in a "detached" state, HEAD points directly to a specific commit.

</details>
<br>

<details>
<summary>When do I use Git stash?</summary>

You use git stash in Git when you need to temporarily save changes in your working directory without committing them. This is typically done in scenarios where you want to switch to a different branch, pull changes from a remote repository, or perform some other operation that requires a clean working directory<br><br>

Here are common situations when you should use git stash:<br>

**Switching Branches**: When you're working on one branch and need to switch to another, but you have uncommitted changes in your working directory. Using git stash allows you to save those changes, switch branches, and then later apply the changes to the new branch.<br><br>

```bash
git stash        # Save changes
git checkout another-branch   # Switch branches
git stash apply  # Apply saved changes to the new branch

```
<br>

**Pulling or Fetching Changes**: Before pulling or fetching changes from a remote repository, you can stash your local changes to ensure a clean working directory. This helps prevent conflicts that might arise when Git tries to merge the incoming changes with your local modifications.<br><br>

```bash
git stash        # Save changes
git pull origin main   # Pull changes from the remote
git stash apply  # Apply saved changes to your working directory
```
<br>

**Temporary Changes**: If you're working on a feature but need to make a quick fix or test something unrelated, you can stash your current changes before making the temporary changes. Afterward, you can apply the stashed changes back.<br><br>

```bash
git stash        # Save feature changes
# Make and test quick fix or unrelated changes
git stash apply  # Apply saved feature changes back
```
<br>

**Resolving Conflicts**: When resolving merge or rebase conflicts, git stash can help. You can stash your changes, then perform the merge or rebase. After resolving conflicts, you can apply your stashed changes again.<br>

```bash
git stash        # Save changes
# Resolve conflicts during merge or rebase
git stash apply  # Apply saved changes after conflicts are resolved
```

</details>
<br>

<details>
<summary>What does git reset do?</summary>

`git reset` is a Git command used to move the HEAD and optionally the index (staging area) to a specified commit. It has different modes, including soft (moves HEAD only), mixed (default, moves HEAD and unstages changes), and hard (moves HEAD, unstages changes, and discards changes in the working directory). You can use it to unstage changes, move the branch pointer, undo commits, and amend the last commit. Use it carefully as it can affect commit history.<br><br>

Here are the primary functions of `git reset`:

- Unstaging Changes<br>
- Moving the HEAD<br>
- Undoing Commits: git reset<br>
- Mixed-Mode for Amend<br>


</details>
<br>

<details>
<summary>What is Git fork? What is difference between git fork, clone and branch?</summary>

- **Git Fork**: Creating a copy of a repository on a Git hosting platform, often for collaborative contributions.
- **Git Clone**: Creating a local copy of a Git repository from a remote, enabling local development.
- **Git Branch**: Creating separate lines of development within a repository, typically for features or bug fixes.

</details>
<br>

<details>
  <summary>What is difference between `git stash pop` and `git stash apply`?</summary>
  
- `git stash pop` applies and removes the most recent stash.
- `git stash apply` applies the most recent stash but leaves it in the stash list for future use or reference.git stash pop applies and removes the most recent stash.
  
</details>
<br>

#### Advanced:

<details>
<summary>I need to update my local repos, what commands do I use?</summary>


- Use `git fetch` to retrieve remote changes.
- Choose to merge with `git merge` or rebase with `git rebase`.
- Resolve conflicts if any.
- Optionally, push local changes with git push to update the remote repository.

</details>
<br>

<details>
<summary>I need to rollback to a previous commit and I don't need my recent changes, what do I use?</summary>

- `git reset --hard <commit>`

</details>
<details>
<summary>How can I amend an older commit?</summary>

- Use `git rebase -i <commit>~1` to start an interactive rebase.
- Change "pick" to "edit" for the commit you want to amend.
- Make your changes and stage them with `git add .`
- Use `git commit --amend` to update the commit.
- Continue the rebase with `git rebase --continue`

</details>
<br>

<details>
<summary>What is the command to check the difference between two commits?</summary>

`git diff <commit1> <commit2>`


</details>
<br>

<details>
<summary>When do you use `git rebase` instead of `git merge`?</summary>

- Use `git rebase` instead of `git merge` when you want to create a cleaner, linear commit history, squash commits, or integrate changes from one branch into another. Use `git merge` when preserving the branch's history is more important, especially in collaborative scenarios.

</details>
<br>

<details>
<summary>Do you know how to undo a git rebase?</summary>

- Use `git reflog` to find the commit hash before the rebase.
- Run `git reset --hard <commit-hash>` to reset your branch to that commit.
- Optionally, force push to update the remote branch if necessary.

</details>
<br>

<details>
<summary>How do you bring down updates from main branch if your local branch becomes stale?</summary>

- Use `git checkout <branch-name>` to switch to your local branch.
- Run `git fetch` to get the latest changes from the remote repository.
- Choose either `git merge main` or `git rebase main` to integrate the updates (pick one based on your workflow).
- Resolve any conflicts if they arise during the merge or rebase.
- Test your branch thoroughly to ensure it works with the latest changes.
- Commit and push your changes if necessary (`git commit` and `git push origin <branch-name>`).

</details>
<br>
