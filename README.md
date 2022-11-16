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

## Solution
Create a [CI job that rebases the release branch to the master](/.github/workflows/rebase-release.yml).

## How to use workflow

1. Ensure you [create a personal access
token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
with the access to the target repository and `contents` permission.
1. Replace [release-1](/.github/workflows/rebase-release.yml#L12) with your release branch.
1. Replace [main](/.github/workflows/rebase-release.yml#L17) with your main branch name.
1. Navigate to the `Actions` tab of your repository, pick `Rebase the release branch` and trigger `Run workflow` on branch.
