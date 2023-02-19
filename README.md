# bare-bones-test

This is a sandbox repo for the Git Bare Bones presentation.

### First command line session:  The happy path change

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

