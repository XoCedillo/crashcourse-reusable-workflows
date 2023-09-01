# crashcourse-reusable-workflows

This is a small repo that contains a small reusable workflow to be used as a playground to understand how reusable workflows and composite actions work.

The structure of the repo is the following:

```
.
├── .github
│   └── workflows
│       └── main.yml
├── README.md
├── action.yml
├── deps
│   └── action.yml
├── lint
│   └── action.yml
└── test
    └── action.yml
```

## Reusable Workflow
- .github/workflows/main.yml:
  This is the so call Reusable workflow, you can call this workflow from other actions to reuse it. Reusable workflow must be under `.github/workflows` and use the directive `on: workflow_call:`. See https://docs.github.com/en/actions/using-workflows/reusing-workflows


## Composite actions
Composite actions allow to group multiple steps into a single action in a way that these bundle of commands become a reusable action to be used in multiple workflows as wished. See https://docs.github.com/en/actions/creating-actions/about-custom-actions#composite-actions

In this repository there are 4 composite actions, 
one main action where other actions are called, and 3 composite actions where the basic steps to run an specific check are encapsulated.

### Main action 
- ./action.yml:
  Main action that calls either the lint of test action depending on the input command

### Reusable actions
- deps/action.yml:
  Install Go dependencies

- test/action.yml:
  Run `gotest`

- lint/action.yml:
  Run `golang-lint`