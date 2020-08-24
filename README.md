# 👋 Github Actions

This repository is just a test repo for testing github actions.

<table>
    <tr><td width=60% valign=top>
        
* Contents
    * [echo Hello in ubuntu](#echo-hello-in-ubuntu)
    * [Comment on Issues](#comment-on-issues)
    * [Get a list of files changed on PR](#get-a-list-of-files-changed-on-pr)
    * [Search on stackoverflow.com](#search-on-stackoverflowcom)
    * [Make a tag whenever the version changes](#make-a-tag-whenever-the-version-changes)
</td></tr>
</table>

## [echo Hello in ubuntu](https://github.com/Alfex4936/github-actions/blob/master/.github/workflows/blank.yml)

This action returns nothing, just echo texts in ubuntu os

```yml
# Controls when the action will run. Triggers the workflow on push or pull request
# events but only for the master branch

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
    
jobs:
    ...
    - name: Run a one-line script
      run: echo Hello, world!
    ...
```

## [Comment on Issues](https://github.com/Alfex4936/github-actions/blob/master/.github/workflows/comment-on-issues.yml)

Testing an action from [@neverendingqs](https://github.com/neverendingqs)

This action leaves a comment by a bot whenever someone makes a issue.

Result is [here](https://github.com/Alfex4936/github-actions/issues/1)

```yml
on:
  issues:
    types: [opened]
    
jobs:
  comment:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/github-script@v3
        with:
          github-token: ${{secrets.GITHUB_TOKEN}}
          script: |
            github.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '👋 Thanks for reporting!'
            })
```

## [Get a list of files on PR](https://github.com/Alfex4936/github-actions/blob/master/.github/workflows/get-list-file-of-pr.yml)

This action echos a list of files in pull request in virtual environment

Check out the result on [here](https://github.com/Alfex4936/github-actions/actions)

```yml
on:
  issue_comment:
    types: [created]
    
jobs:
  ask-stackoverflow:
    runs-on: ubuntu-latest
    steps:
      - uses: neverendingqs/gh-action-ask-stackoverflow@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## [Search on stackoverflow.com](https://github.com/Alfex4936/github-actions/blob/master/.github/workflows/search-on-stackoverflow.yml)

Testing an action from [@neverendingqs](https://github.com/neverendingqs)

This action leaves a comment by a bot whenever someone comments '/so something' on PR or issues

Result is [here](https://github.com/Alfex4936/github-actions/issues/1)

```yml
on:
  issue_comment:
    types: [created]
    
jobs:
  ask-stackoverflow:
    runs-on: ubuntu-latest
    steps:
      - uses: neverendingqs/gh-action-ask-stackoverflow@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## [Make a tag whenever the version changes](https://github.com/Alfex4936/github-actions/blob/master/.github/workflows/tag-new-npm-pkg.yml)

Testing an action from [@neverendingqs](https://github.com/neverendingqs)

This action makes a tag in branch whenever we change the package version in package.json 

Result is [here](https://github.com/Alfex4936/github-actions/tree/v0.0.2)

```yml
on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
    
jobs:
    ...
    - name: Run a one-line script
      run: echo Hello, world!
    ...
```
