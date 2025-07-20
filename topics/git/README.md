# Git

## Exercises

| Name              | Topic  | Objective & Instructions         | Solution                                    | Comments |
| ----------------- | ------ | -------------------------------- | ------------------------------------------- | -------- |
| My first Commit   | Commit | [Exercise](commit_01.md)         | [Solution](solutions/commit_01_solution.md) |          |
| Time to Branch    | Branch | [Exercise](branch_01.md)         | [Solution](solutions/branch_01_solution.md) |          |

## Questions

### Git Basics

<details>
<summary>How do you know if a certain directory is a git repository?</summary><br><b>
You can check if there is a ".git" directory.
</b>
</details>

<details>
<summary>What is <code>git pull</code>?</summary><br><b>

Shortly, git pull = git fetch + git merge

When you run git pull, it gets all the changes from the remote or central
repository and attaches it to your corresponding branch in your local repository.

</b></details>

<details>
<summary>Explain what the file <code>gitignore</code> is used for</summary><br><b>
The purpose of <code>gitignore</code> files is to ensure that certain files not tracked by Git remain untracked. To stop tracking a file that is currently tracked, use git rm --cached.
</b>
</details>

<details>
<summary>How can you see which changes have done before committing them?</summary><br><b>
`git diff`

</b></details>

<details>
<summary>What <code>git status</code> does?</summary><br><b>

`git status` helps you to understand the tracking status of files in your repository. Focusing on working directory and staging area - you can learn which changes were made in the working directory, which changes are in the staging area and in general, whether files are being tracked or not.
</b></details>

<details>
<summary>You've created new files in your repository. How to make sure Git tracks them?</summary><br><b>

`git add FILES`
</b>
</details>

### Scenarios

<details>
<summary>You have files in your repository you don't want Git to ever track them. What should you be doing to avoid ever tracking them?</summary><br><b>

Add them to the file `.gitignore`. This will make sure these files are never added to staging area.
</b></details>


### Branches

<details>
<summary>Common DevOps branching strategies</summary><br><b>

Gitflow is the most widely known branching strategy that takes a multi-branch approach to managing source code. This approach consists of two main branches that live throughout the development lifecycle: master and develop.

Primary Branches

  - Master. This is the primary branch where all the production code is stored. Once the code in the “develop” branch is ready to be released, the changes are merged to the “master” branch and used in the deployment.
  - Develop. This is where all the actual development happens. All the pre-production code is stored here, and the completed code of all the supporting branches is merged directly to the “develop” branch.

Support Branches

During development, developers create different branches for specific use cases using the “develop” branch as the base. The following are examples of some support branches:

  - Feature. This branch is used to develop new features and branches off from the “develop” branch.
  - hotfix. This is the branch to deal with production issues where quick fixes are required. It can branch off from the “master” itself, but needs to be merged to both “master” and “develop” branches.
  - Release. This branch is used to aggregate fixes and improvements, and prepare for the production release. It will branch off the “develop” branch and merge to both “develop” and “master.”

</b></details>


<details>
<summary>You have two branches - main and devel. How do you make sure devel is in sync with main?</summary><br><b>
<code>
```
git checkout main
git pull
git checkout devel
git merge main
```
</code>

</b></details>

### Merge

<details>
<summary>You have two branches - main and devel. How do you merge devel into main?</summary><br><b>

```
git checkout main
git merge devel
git push origin main
```

</b></details>

<details>
<summary>How to resolve git merge conflicts?</summary><br><b>

<p>
First, you open the files which are in conflict and identify what are the conflicts.
Next, based on what is accepted in your company or team, you either discuss with your
colleagues on the conflicts or resolve them by yourself
After resolving the conflicts, you add the files with `git add <file_name>`
Finally, you run `git rebase --continue`
</p>
</b></details>

### Rebase

<details>
<summary>How do you remove a remote branch?</summary><br><b>

You delete a remote branch with this syntax:

git push origin :[branch_name]
</b></details>

<details>
<summary>How do you discard local file changes? (before commit)</summary><br><b>

`git checkout -- <file_name>`
</b></details>

<details>
<summary>How do you discard local commits?</summary><br><b>

`git reset HEAD~1` for removing last commit
If you would like to also discard the changes you `git reset --hard``
</b></details>


## References


## Git Diff

<details>
<summary>What git diff does?</summary><br><b>

git diff can compare between two commits, two files, a tree and the staging area, etc.
</b></details>



## Git Internal

