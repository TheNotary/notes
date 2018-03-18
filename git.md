# Git

###### Concept of Commits and Branches

You can make changes to the source code of a project in increments.  For instance, if you add a feature to an existing project, you can effectively bottle up these changes (aka **change sets**) into commit.  That's really all a commit is, an addition and/ or deletion of text to a project.  Whenever you make a new commit, you are doing so under a branch.  All commits live under a branch.  The default branch for a project is named `master`.

The easiest way to share new commits you've made with your team is via the below process:

1. Create a new branch named after the thing you're working on (we call these types of branches a feature branch)
2. Commit your desired changes under this branch
3. Push your feature branch up to your teams central github repo
4. Click the Github buttons in your browser to create a new `Pull Request` (PR) out of your branch
5. Message a team mate to have your changes reviewed/ approved/ merged into the master branch

## Cheatsheet!

### Commiting
* `git add -A` - adds all files to staging area
* `git commit -m "<MESSAGE>"` - commits changes with a brief description message about the changes
* `git commit --amend` - amends the last commit with everything in the staging area
* `git reset HEAD^` - undoes the last commit

### Navigating
* `git checkout <COMMIT/ BRANCH>` -  Switches you to a different branch to work on
* `git checkout -b <NAME>` - creates a new branch and changes into it
* `git branch <NAME>` - creates a new branch

### Colaborating
* `hub create` - logs into Github and creates a remote repository
* `git remote -v` - lists the remote names and their locations
* `git remote add upstream` - for pulling down the updated repository

### Monitoring
* `git status` - shows state of working directory
* `glg` - better log
* `git log` - shows list of commits
