# Github Actions

- It is a **continuous integration & continuous delivery (CI/CD)** platform that allows you to automate your build, test, and deployment pipeline.
- It uses YAML syntax to define the workflow.
- Each workflow is stored as a separate YAML file in your code repository, in a directory named `.github/workflows`.

## Components of Github Actions

#### Workflows

- A workflow is a **configurable automated process** that will run one or more jobs. Workflows are defined by a `YAML` file checked in to your repository and will run when triggered by **an event** in your repository, or they can be triggered manually, or at a defined schedule.
- A repo can have multiple workflows, each of which can perform a different set of tasks.

#### Events

- An event is a specific activity in a repository that triggers a workflow run.

#### Jobs

- A job is **a set of steps** in a workflow that is executed on the same runner.
- Each step is either a shell script that will be executed, or an _action_ that will be run.
- Steps are executed in order and are dependent on each other.

#### Actions

- An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task.

#### Runners

- A runner is a server that runs your workflows when they're triggered.
- Each runner can run a single job at a time.
- GitHub provides **Ubuntu Linux, Microsoft Windows, and macOS runners** to run your workflows; each workflow run executes in a fresh, newly-provisioned virtual machine.

> An event will not be created when you push more than three tags at once.

- **Example**

```yaml
name: learn-github-actions
run-name: ${{ github.actor }} is learning GitHub Actions
on: [push]
jobs:
  check-bats-version:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: "14"
      - run: npm install -g bats
      - run: bats -v
```
