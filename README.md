# Keep scheduled workflow activity

With this GitHub Action, scheduled workflow won't be disabled even if there's no recent activity in the repository.

English | [简体中文](README.zh-CN.md)

## Why

In GitHub, scheduled workflows are automatically disabled when no repository activity has occurred in 60 days.

## Usage

```yml
name: Keep scheduled workflow activity

on:
  schedule:
    - cron: "0 0 * * *" # 00:00 UTC every day

jobs:
  keep-scheduled-workflow-activity:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Keep scheduled workflow activity
        uses: WaterLemons2k/scheduled-workflow-activity-action@v1
```

## Inputs

All inputs are optional.

| Input     | Description                                                  | Default                                                 |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------- |
| `name`    | Username used for commit.                                    | `github-actions[bot]`                                   |
| `email`   | Email address used for commit.                               | `41898282+github-actions[bot]@users.noreply.github.com` |
| `message` | Commit message for the repository.                           | `chore: empty commit`                                   |
| `days`    | Number of days between the latest commit and the new commit. | `50`                                                    |
| `push`    | Whether to push a new commit.                                | `true`                                                  |