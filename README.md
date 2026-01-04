# Git Katas

## Start

![Quick Start](/images/quickstart.gif)

- Clone this repository
- Go into the folder you want to solve an exercise in
- Run the `setup.sh` script
- Consult the README.md in that folder to get a description of the exercise

### Basic Git Katas

1. [basic-commits](basic-commits/README.md) - Very basic creation of commits.
1. [basic-staging](basic-staging/README.md) - Interacting with the stage (index).
1. [basic-branching](basic-branching/README.md) - The first stride into branching.
1. [ff-merge](ff-merge/README.md) - A tour around the most trivial of merges.
1. [3-way-merge](3-way-merge/README.md) - A basic merge, involving multiple diverged branches.
1. [merge-conflict](merge-conflict/README.md) - A basic merge between diverging branches with incompatible (but simple) changesets.
1. [merge-mergesort](merge-mergesort/README.md) - A merge conflict with actual code.
1. [rebase-branch](rebase-branch/README.md) - Using rebase as an alternative to merging.
1. [basic-revert](basic-revert/README.md) - Use revert to revert a change
1. [reset](reset/README.md) - Reset is a powerful and slightly dangerous command if you do not know what you are doing. Go through the three modes of resetting here.
1. [basic-cleaning](basic-cleaning/README.md) - Cleaning the workspace.
1. [amend](amend/README.md) - Amending previous commits.
1. [reorder-the-history](reorder-the-history/README.md) - We might have created our commits in a suboptimal order, practice to fix that scenario here.
1. [squashing](squashing/README.md) - A lot of small commits is good when you are working locally, but for sharing your code, it might be more beneficial to deliver your code changes in large sets. Go here to experiment with that. Write a good commit
1. [advanced-rebase-interactive](advanced-rebase-interactive/README.md) - Practice using the interactive rebase commands.
1. [basic-stashing](basic-stashing/README.md) - The first stride into stashing.
1. [ignore](ignore/README.md) - The basics of using the `.gitignore` file. And using `git rm`.
1. [submodules](submodules/README.md) - Submodules are loathed by many. Run through this exercise to see what the ruckus is all about.
1. [git-tag](git-tag//README.md) - Tags are convenient for keeping track of commits that bump a version number. In this exercise, you will list, add and delete tags.

### Katas that solve standard problems

1. [commit-on-wrong-branch](commit-on-wrong-branch/README.md) - If we accidentally put unpushed commits on the wrong branch, how do we effectively _move_ them to another branch before our work on that branch.
1. [commit-on-wrong-branch-2](commit-on-wrong-branch-2/README.md) - Another exercise on what to do if you have accidentally committed on the wrong branch.
1. [save-my-commit](save-my-commit/README.md) - Should you accidentally or on purpose delete a commit, go here to try and save it. You will use the reflog.
1. [detached-head](detached-head/README.md) - git complains that you are in a "You are in 'detached HEAD' state". What do you do?
1. [change-author](change-author//README.md) - Change the author of commits

### Katas On Advanced features

1. [reverted-merge](reverted-merge/README.md) - We revert a merge, but, after fixes are added to the merged branch, we want the changes from merge and the new fixes.
1. [bad-commit](bad-commit/README.md) - Using `git bisect` to find a bad commit.
1. [bisect](bisect/README.md) - Another kata using `git bisect`.
1. [pre-push](pre-push/README.md) - A quick exercise in using Git hooks.
1. [Investigation](investigation/README.md) - Discover what is going on in a Git repo, figure out what it looks like under the hood.
1. [rebase-exec](rebase-exec/README.md) - Run tests on every commit using `git rebase --exec`

## Cheatsheet

A collection of useful commands to use throughout the exercises:

```shell
# Initializing an empty git repository.
git init            # Initialize an empty git repository under current directory.

# Cloning a repository
git clone https://github.com/praqma-training/git-katas.git      # Clone this repository to your current working directory

# Git (user and repo level) configurations
git config --local user.name "Repo-level Username"          # For setting a local git repo level user name.
git config --local user.email "Repo-level.Email@Example.com" # For setting a local git repo level user email.
                                                            # --global -> User level git config stored in <user-home>/.gitconfig for e.g. ~/.gitconfig
                                                            # --local -> repo level config stored in repo's main dir under .git/config


# See local changes
git status                  # Show the working tree status
git diff                    # Show changes current working directory (not yet staged)
git diff --cached           # Show changes currently staged for commit

# Add files to staging (before a commit)
git add myfile.txt          # Add myfile.txt to stage
git add .                   # Add entire working directory to stage

# Make a commit
git commit                              # Make a new commit with the changes in your staging area. This will open an editor for a commit message.
git commit -m "I love documentation"    # Make a new commit with a commit message from the command line
git commit -a                           # Make a new commit and automatically "add" changes from all known files
git commit -am "I still do!"            # A combination of the above
git commit --amend                      # Re-do the commit message of the previous commit (don't do this after pushing!)
                                        #   We _never_ change "public history"
git reset <file>                        # Unstage a staged file leaving in working directory without losing any changes.
git reset --soft [commit_hash]          # resets the current branch to <commit>. Does not touch the staging area or the working tree at all.
                                        # --hard mode would discard all changes.

# Configuring a different editor
## Avoid Vim but stay in terminal:
- `git config --global core.editor nano`

## For Windows:
- Use Notepad:
`git config --global core.editor notepad`

- or for instance Notepad++:
`git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"`


# See history
git log             # Show commit logs
git log --oneline   # Formats commits to a single line (shorthand for --pretty=oneline  --abbrev-commit )
git log --graph     # Show a graph commits and branches
git log --pretty=fuller     # To see commit log details with author and committer details, if any different.
git log --follow <file>     # List the history of a file beyond renames
git log branch2..branch1    # Show commits reachable from branch1 but not from branch2

# Deferring
git stash                               # Stash (store temporarily) changes in working branch and enable checkingout a new branch
git stash list                          # List stored stashes.
git stash apply <stash>                 # Apply given <stash>, or if none given the latest from stash list.


# Working with Branches
git branch my-branch       # Create a new branch called my-branch
git switch my-branch     # Switch to a different branch to work on it
git switch -c my-branch  # Create a new branch called my-branch AND switch to it
git branch -d my-branch    # Delete branch my-branch that has been merged with master
git branch -D my-branch    # Forcefully delete a branch my-branch that hasn't been merged to master

# Merging
git merge master         # Merge the master branch into your currently checked out branch.
git rebase master        # Rebase current branch on top of master branch

# Working with Remotes
git remote              # Show your current remotes
git remote -v           # Show your current remotes and their URLs
git push                # Publish your commits to the upstream master of your currently checked out branch
git push -u origin my-branch  # Push newly created branch to remote repo setting up to track remote branch from origin.
                              # No need to specify remote branch name, for e.g., when doing a 'git pull' on that branch.
git pull                # Pull changes from the remote to your currently checked out branch

# Re/moving files under version control
git rm <path/to/the/file>                 # remove file and stage the change to be committed.
git mv <source/file> <destination/file>   # move/rename file and stage the change to be committed.

# Aliases - it's possible to make aliases of frequently used commands
#   This is often done to make a command shorter, or to add default flags

# Adding a shorthand "sw" for "switch"
git config --global alias.sw "switch"
# Usage:
git sw master     # Does a "git switch master"

## Logging
git log --graph --oneline --all # Show a nice graph of the previous commits
## Adding an alias called "lol" (log oneline..) that shows the above
git config --global alias.lol "log --graph --oneline --all"
## Using the alias
git lol     # Does a "git log --graph --oneline --all"
```

## Testing

There is a very small test that you can run in powershell or bash.
It is contained in the scripts `test.sh` and `test.ps1`.

### Cleanup

You can remove testing artifacts, `exercise` directories, with the git clean command:

```sh
git clean -ffdX
```
