### Problem
Pulled the same branch name from two (2) remote repos. Which led to conflicts on `git checkout`.

### Solution
Delete the unwanted remote tracking branch in order to checkout to the correct branch.

- list the remote branches and identify the unwanted remote tracking branch
	`git branch -r`
- delete the unwanted remote tracking branch
	`git branch -d -r <remote>/<branch-name>` 
