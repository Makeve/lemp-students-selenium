[Back to Home](../README.md)

# Collaborative Workflows

## Introduction

Collaborative workflows in Git allow multiple developers to work on the same project simultaneously. This guide covers common workflows like GitFlow and Forking Workflow.

## Step-by-Step Guide

### GitFlow

GitFlow is a branching model that defines a strict branching structure.

#### Steps

1. **Start a New Feature**:
   - Open your terminal.
   - Navigate to your Git repository:
     ```sh
     cd path/to/your/repository
     ```
   - Create and switch to a feature branch:
     ```sh
     git checkout -b feature/<feature_name> develop
     ```

2. **Finish the Feature**:
   - Switch to the develop branch:
     ```sh
     git checkout develop
     ```
   - Merge the feature branch:
     ```sh
     git merge feature/<feature_name>
     ```

3. **Start a Release**:
   - Create and switch to a release branch:
     ```sh
     git checkout -b release/<release_name> develop
     ```

4. **Finish the Release**:
   - Switch to the master branch:
     ```sh
     git checkout master
     ```
   - Merge the release branch:
     ```sh
     git merge release/<release_name>
     ```
   - Switch to the develop branch and merge the release branch:
     ```sh
     git checkout develop
     git merge release/<release_name>
     ```

5. **Start a Hotfix**:
   - Create and switch to a hotfix branch:
     ```sh
     git checkout -b hotfix/<hotfix_name> master
     ```

6. **Finish the Hotfix**:
   - Switch to the master branch:
     ```sh
     git checkout master
     ```
   - Merge the hotfix branch:
     ```sh
     git merge hotfix/<hotfix_name>
     ```
   - Switch to the develop branch and merge the hotfix branch:
     ```sh
     git checkout develop
     git merge hotfix/<hotfix_name>
     ```

### Forking Workflow

The Forking Workflow involves creating a personal copy (fork) of the repository and making changes there.

#### Steps

1. **Fork the Repository**:
   - On GitHub, click the "Fork" button to create a personal copy of the repository.

2. **Clone Your Fork**:
   - Open your terminal.
   - Navigate to the directory where you want to clone the repository:
     ```sh
     cd path/to/desired/directory
     ```
   - Clone your fork:
     ```sh
     git clone <your_fork_url>
     ```

3. **Add the Original Repository as a Remote**:
   - Navigate to your forked repository:
     ```sh
     cd path/to/your/forked/repository
     ```
   - Add the original repository as a remote:
     ```sh
     git remote add upstream <original_repo_url>
     ```

4. **Fetch Changes from the Original Repository**:
   - Fetch changes from the upstream repository:
     ```sh
     git fetch upstream
     ```

5. **Create a Branch for Your Changes**:
   - Create and switch to a new branch:
     ```sh
     git checkout -b <branch_name>
     ```

6. **Make and Commit Changes**:
   - Make your changes and commit them:
     ```sh
     git add <file>
     git commit -m "Your commit message"
     ```

7. **Push Changes to Your Fork**:
   - Push the changes to your fork:
     ```sh
     git push origin <branch_name>
     ```

8. **Create a Pull Request**:
   - On GitHub, create a pull request to merge changes from your fork into the original repository.

---

<div style="width: 100%">
<a href='resolving-conflicts.md'><-- Previous Section: Resolving Conflicts</a>
<div align="right"><a href='commit-best-practices.md'>Next Section: Commit Best Practices--></a></div>
</div>
