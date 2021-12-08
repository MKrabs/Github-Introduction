# Github-Introduction
E-Portfolio about GitHub and it's management tools / workflows

Welcome to my small E-Portfolio about Github. I will try to explain the basics of GitHub, what it can do to ease your workflows and how it can help you managing your projects with you and your team.

### Requierments
- [x] A web-browser
- [x] an Internet connection
- [x] (optional) own server - raspberry Pi
- [ ] (optional) a multi-million dollars app idea
- [ ] (optional) a team to work with

## Pull requests
When working on a Project, you don't want the entire team to work simultaneously on the same files, and cause massiv headaches figuring out who changed what, when and why. Working with branches to seperate work is a good solution to this. Once done with the work, one might want to add the changes to `main` and rebase the project. This process is called `pulling`, which can be done either manually, or through `pull requests`. For this basic task, go to:

1. https://github.com/Owner/repo
2. `Pull Requests` (3rd option)
3. New Pull Request
4. into branch &#8592; from branch
5. Create Pull Request

And that's all.. No preconditions to satisfy to be able to pull into a branch.

But what if you want the code going into a branch to be always "bug free" and have some minimum _test coverage_ (or other arbitrary metric)?

[Learn more about pull requests &#8594;](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)

## Branch protection
As the name might suggest, branch protection is what protects a branch. A set of rules that apply when X happens (or wants to happen).

1. https://github.com/Owner/repo
2. `Settings` (last option, only accessible by the admin (or admins if the repo is in an Organisation))
3. Branches
4. Add Rule

From there on you can create custom rules for individual (or multiple) branches. Many rules such as `Require a pull request before merging`, `Require approvals` or (the best option personally) `Require status checks to pass before merging` can be selected and adjusted to ones liking. `Require status checks to pass before merging` for example will only allow merging when some 'actions' have **passed**. 

[Learn more about branch protection &#8594;](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests)

## Workflows
GitHub workflows are scripts that run whenever they are called: either after a push or when a pull request is triggered, or manually if you're feeling frisky. The scripts run specified code (often your own code) and return the success status (success, failure, abtortion). The workflows are part of the whole GitHub Actions service to help you automate a lot of boring / repetitive stuff.

Go to https://github.com/Owner/repo/tree/branch/.github/workflows, to find all your Workflows as `.yml` files.

```
# This is a basic workflow to help you get started with Actions
name: CI

# Controls when the workflow will run
on:

  # Triggers the workflow on push or pull request events but only for the main branch
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:

  # This workflow contains a 2 jobs called "build" and "test"
  build:
  
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2

      # Runs a single command using the runners shell
      - name: Run a one-line script
        run: echo Hello, world!
          
  test:
    runs-on: ubuntu-latest
    
    steps:
    
      - uses: actions/checkout@v2

      # Runs a set of commands using the runners shell
      - name: Run a multi-line script
        run: |
          echo Add other actions to build,
          echo test, and deploy your project.
```

[Learn more about workflows and actions &#8594;](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)


## Self runner
This chapter is more of a personal thing to do, but I prefer hosting my own GitHub runner instead of having it all in the cloud. To do this I have my raspberry Pi running the GitHub Actions script running and executing all the workflows on it (the `.yml` files will specify on which runner a job will run).

To do this follow the instructios for your individual runner: https://github.com/Owner/repo/settings/actions/runners/new (you need to be admin for this)

Find the runners architecture with `dpkg --print-architecture` and select it on the instructions from above, copy the code snippets into the runners terminal and watch it do wonders.

```
--------------------------------------------------------------------------------
|        ____ _ _   _   _       _          _        _   _                      |
|       / ___(_) |_| | | |_   _| |__      / \   ___| |_(_) ___  _ __  ___      |
|      | |  _| | __| |_| | | | | '_ \    / _ \ / __| __| |/ _ \| '_ \/ __|     |
|      | |_| | | |_|  _  | |_| | |_) |  / ___ \ (__| |_| | (_) | | | \__ \     |
|       \____|_|\__|_| |_|\__,_|_.__/  /_/   \_\___|\__|_|\___/|_| |_|___/     |
|                                                                              |
|                       Self-hosted runner registration                        |
|                                                                              |
--------------------------------------------------------------------------------
```

All the work is automated, what is this "work" we have to do. 

# Project

GitHub provides a nice way of creating, managing and integrating Tasks, Notes, Pullrequest and Boards, to organise and handle large amounts of work into one (or more) places.

## Issues
Issues are the most basic form of tracking work / todos. When Issues are open, work is not finished.

## Mile Stones

## Boards

You can find your own board under https://github.com/Owner/repo/projects

[Learn more about project boards &#8594;](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/about-project-boards)

## Project tickets
 - Ticket with issues
 - Ticket with checkboxes
