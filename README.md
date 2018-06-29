# GitHub Training Scripts

This directory contains several scripts used to set up and facilitate our classes.

## First Time Usage

### Remote Configuration

To use these scripts, please follow these steps **first**:

- [ ] Create an organization that will house all student repositories. Something like "githubtraining" or "githubschool" will work, but any name will work.
- [ ] If you're using GitHub Enterprise, and access to github.com is limited within your organization, import the following repos and all their branches in your newly created organization: [caption-this](https://github.com/githubtraining/caption-this), [polygons](https://github.com/githubtraining/polygons), [github-games](https://github.com/githubtraining/github-games). You'll need access to GitHub.com to perform this one-time operation.
- [ ] Ensure your user account is an owner of the newly created training org, and add any other trainers as owners of the org. Alternatively, you can create a separate teaching account that all trainers have access to, and make that teaching account an owner of the org.
- [ ] Create a [Personal Access Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) for your user account, or the shared teaching account. You'll need this for the [local configuration](#local-configuration).
- OPTIONAL: If using Survey Gizmo to distribute surveys to participants, [generate an API key and secret](https://apihelp.surveygizmo.com/help/authentication). Save these for later. 
- OPTIONAL: If you're going to offer participants one-on-one appointments, determine the URL participants will use to schedule those. We use [YouCanBook.me](http://youcanbook.me). You'll need the URL later.

### Local Configuration

Generally speaking, we'll create a `.trainingmanualrc` in your home directory, and source that file from your Bash or ZSH profile. The scripts take care of doing that for you. When performing an operation using the training scripts, the variables specified in your `~/.trainingmanualrc` file will be used.

Here's how to get your local environment up and running: 

1. install [jq](https://stedolan.github.io/jq/download/)
2. run `script/teach-class` and choose option 0 to set up your environment variables. You'll need the following pieces of information from [above](#remote-configuration):
   - the title of your newly created training organization
   - your username, or the username of a shared teaching account
   - your personal access token (PAT) or the PAT of the shared teaching account
   - (optional) the API key and secret for Survey Gizmo
   - (optional) the URL for one-on-one appointments
3. exit your terminal session and start a new one
4. run `script/teach-class` and choose the option for the task you need

## Class Scripts

### script/teach-class

This script is used to run an entire class and is comprised of some of the scripts that are identified below.

**Usage:** `script/teach-class`

> Note: 
> This requires [jq](https://stedolan.github.io/jq/) to be installed. Installation instructions are provided [here](https://github.com/stedolan/jq/wiki/Installation). The first time you execute `script/teach-class`, choose option `**0**` to configure the script within your organization.


### script/new-virtual

_This is contained within the `teach-class` script._

This script is used to create a new class repository for GitHub for Developers based on the class template based on the virtual class content.

**Usage:** `script/new-virtual REPO-NAME`

### create-conflict-repos

_This is contained within the `teach-class` script._

This script is used to create a unique repository for each user to practice resolving merge conflicts. It pulls the names from the repository used on day 1.

**Usage:** `script/create-conflict-repos`

### check-conflict-repos

_This is contained within the `teach-class` script._

This script is used to check whether students have resolved the merge conflicts in their individual repos and writes those results back to the day 1 repo.

**Usage:** `script/check-conflict-repos`

### create-game-repos

_This is contained within the `teach-class` script._

This script is used to create an individual game repository for each student where they will learn how troubleshoot using log, show, diff, bisect, etc. It pulls the names from the repository used on day 1 and will also create a repo for githubteacher.

**Usage:** `script/create-game-repos`

### check-game-repos

This script is used to determine whether the students successfully fixed their game and writes those results back to the day 1 repo.

**Usage:** `script/check-game-repos`

### reset-game

This script is used to reset the github-games repository in githubschool using the template in githubtraining. It will also delete the copy of the game from the githubteacher account.

**Usage:** `script/reset-game`