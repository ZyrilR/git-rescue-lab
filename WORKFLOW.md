# Git Rescue Workflow



## 1. Bisect Finding



The first bad commit was `c99fb4209e6fb6e5ed2789893fdb2f893d61d6c6`. It changed the BULK20 condition from `items.length >= 5` to `items.length > 5`, causing orders with exactly 5 items to miss the 20% discount.



## 2. Recommended Branching Strategy



For a team of four, I recommend GitHub Flow. It uses short-lived feature branches and pull requests while keeping `main` stable. It has less process overhead than Git Flow and provides more structure for code review than committing directly to a shared trunk.



## 3. Removing the Secret from Git History



Adding `.env` to `.gitignore` and using `git rm --cached .env` prevents the file from being tracked in future commits, but the secret remains in older commits. Fully removing it would require rewriting Git history with a tool such as `git filter-repo` or BFG and force-pushing the rewritten history. If the secret were real, it should also be revoked or rotated. This assignment does not require rewriting the old history.



## 4. History Rewriting



Rewriting history was acceptable in Task 2 because the commits being changed were intended to remain local and had not been shared with teammates. Once a commit has been pulled by teammates, rewriting it changes its commit hash and causes their local histories to diverge, requiring coordination and potentially a force push or rebase.

