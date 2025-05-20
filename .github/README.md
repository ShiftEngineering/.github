# Organization Workflow Templates

This repository contains GitHub workflow templates for our organization.

## Available Workflows

### Issue Tracker Automation

The `issue-tracker.yml` workflow automates issue tracking by moving issues from "In Progress" to "In Review" when a pull request is opened that references those issues.

#### How it works

1. When a pull request is opened, the workflow scans the PR title and body for issue references (e.g., #123).
2. For each referenced issue, it:
   - Adds a comment to the issue indicating it has been moved to "In Review"
   - Uses GraphQL to update the issue's status in any GitHub Projects from "In Progress" to "In Review"

#### Requirements

- The issue must be in a GitHub Project
- The Project must have a "Status" field with "In Progress" and "In Review" options
- The issue must be referenced in the PR title or body with the # symbol (e.g., #123)

### Branch Issue Tracker

The `branch-issue-tracker.yml` workflow automates issue tracking by moving issues to "In Progress" when a branch with the issue number in its name is created.

#### How it works

1. When a branch is created, the workflow extracts issue numbers from the branch name.
2. For each identified issue, it:
   - Adds a comment to the issue indicating it has been moved to "In Progress"
   - Uses GraphQL to update the issue's status in any GitHub Projects from initial statuses like "Todo" or "Backlog" to "In Progress"

#### Requirements

- The issue must be in a GitHub Project
- The Project must have a "Status" field with an "In Progress" option
- The branch name must include the issue number in a common format:
  - `123-feature-description`
  - `feature/123-description`
  - `issue-123`
  - `bugfix/123`
  - Or any other format where the issue number is separated by `/`, `-`, `_`, or at the start of the branch name

## Usage

To use these workflows in your repository, GitHub Actions will automatically suggest them when creating a new workflow.
