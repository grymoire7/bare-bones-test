# bare-bones-test

This is a sandbox repo for the Git Bare Bones presentation.

## First command line session:  The happy path change

Plan: clone repo, create a branch, make changes, push changes, create/merge PR

```bash
# Clone the repository locally... get url from GitHub
git clone git@github.com:grymoire7/bare-bones.git

# Make sure the main branch is up-to-date
git status
git pull

# Switch to a newly created branch
git switch -c TASK-update-repo-metadata

# Make some changes to README.md
vi README.md

# View status/diff, then add changes to the index/staging.
git status
git add -A   # add all changes, new files to staging area
git status
git log      # shows the series of pink dots in this branch

# Commit changes to local repo copy of this branch (make a new pink dot)
git commit -m “include project status in readme”

# Make another change, add it, commit it
vi LICENSE.md # new file
git add -A
git status
git commit -m “add license file”
git status
git log origin/main..HEAD # show commits that have not been pushed

# Push our changes for this branch to origin/remote
git push # do what command it says
git switch main # see that the changes are not here

# Go to GitHub, create pull request, review, merge, delete branch

git pull  # update local/main and workspace see changes have been merged
```

## Second command line session: Undo
Plan: make mistakes, undo them

### Create a commit and completely roll it back
```bash
# Create branch
git switch -c DEV-8776-horrible-ideas

# Edit file
vi README.md
git add -A
git commit -m “Add incorrect readme update”
git commit --amend  # only last commit if not pushed, to update comment
git log
git reset --hard HEAD^ # reset index and working dir to specified commit
```

### Create a commit and roll it back one area at a time
```bash
git reset --soft HEAD^   # not in local repo (committed), but staged (in index)
git log && git status
git restore --staged -- README.md  # not staged, but changes appear in working directory
# same as `git reset -- README.md`
git status
git restore --staged --worktree -- README.md  # changes no longer appear in working directory
# same as `git checkout -- README.md`
git status
```

### Create another commit, push it, then revert it
```bash
vi README.md; git add -A; git commit -m “add a bad idea”; git log; git push
git revert <SHA>  # fragment of SHA
```

### Push a branch, then delete it both remotely and locally
```bash
git push --delete origin DEV-8776-horrible-ideas  # delete remote branch
git switch main
git branch -d DEV-8776-horrible-ideas  # delete local branch
```


