## About

I have seen in multiple repositories with maintained separate release branches,
that master keep being rebased before being merged into the feature branch,
current repo is for trying to reproduce that issue.

## Reproduction

1. Create a feature branch
1. Merge to master.
1. Merge master to release branch.
1. Create a feature branch.
1. Merge feature branch into master.
1. Create PR targeting master to release.

## Expected behavior
Ensure that only 1 commit from second feature is about to be added.
