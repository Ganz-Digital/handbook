---
sidebar_label: Process
---

# How we develop.

## Kanban Boards

We manage our projects with Kanban boards. On these boards, there are cards and columns. The cards represent tasks. The columns describe the stage a task is in.

## Tasks

Every card has a user story. A description of what we want to achieve with the task or a description of something that doesn't work as expected.

## Steps to Completion

After you've received a task, break the user story into smaller steps to completion. Sometimes, there is already a checklist called "Steps to Completion" on a Trello card. If it's not there, create it.

Breaking a task down into checklist items makes sure that you understand it and think about how to do it before actually doing it. It also minimizes the risk that you run into unforeseen dead-ends.

## Time Tracking

For every task, create a timer in JustPressWork with the name of the task and track your time there.

If the card doesn't have a good title that also works as the name of the timer, improve it. If you change it, make sure to update the name of the card in the project board. Inform the person who wrote it after making the change.

## Git Branches

### One branch per task

As a general guideline, we create a new branch for every task (and thus card). The names of the branches should follow this pattern:

- `feature/...`
- `bugfix/...`
- `improvement/...`

`feature/qr-code-checkin`, `bugfix/wrong-timestamp`, `improvement/insurance-form-design` would be valid names.

:::note
It's okay to fix something on master, if the change you make is very small.
:::

:::note
It's okay to re-use an existing branch if the topic is the same.
:::

## Pull Requests

Create a Pull Request when you're ready to merge your code.

Pull requests with changes to the UI (user interface) must have a screencast that shows the UI in action.

## Reviews

### Peer Reviews

When you're done with your task, request a review from your peer. Incorporate their improvement suggestions or decide against them if you think your way of doing it is better.

### Manager Reviews

After the peer review, request a review from your manager.
