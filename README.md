## About

Repositories with maintained separate release branches and rebase merge strategy
master keep being rebased before being merged into the feature branch, current
repo is for trying to create a "safer" automation for that.

## Reproduction

1. Create a feature branch
1. Rebase and merge to main.
1. Rebase and merge main to release branch.
1. Create a feature branch.
1. Rebase and merge feature branch into main.
1. Create PR targeting main to release.

## The problem
When we are rebasing commit into release branch on step 3 we create a unique
commit, which diverges from the one on main branch. Meaning we now are pushing 2
commits on step 6, one of which already exist, but has different HASH.
