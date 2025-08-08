[Back to Home](../README.md)

# Branching and Merging

## Introduction

Branching and merging are essential Git concepts that allow you to work on different features or fixes simultaneously and later combine them.

## Step-by-Step Guide

### Creating a Branch

To create a new branch:

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Create a new branch:
   ```sh
   git branch <branch_name>
   ```

### Switching to a Branch

To switch to an existing branch:

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Switch to the branch:
   ```sh
   git checkout <branch_name>
   ```

### Creating and Switching to a New Branch

To create a new branch and switch to it immediately:

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Create and switch to the new branch:
   ```sh
   git checkout -b <new_branch_name>
   ```

### Viewing Branches

To list all branches in your repository:

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. List all branches:
   ```sh
   git branch
   ```

## Merging

### Merging Branches

To merge changes from one branch into another:

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Switch to the target branch:
   ```sh
   git checkout <target_branch>
   ```
4. Merge the changes from the source branch:
   ```sh
   git merge <source_branch>
   ```

### Resolving Merge Conflicts

Sometimes, Git cannot automatically merge changes, resulting in a conflict. You'll need to resolve these conflicts manually.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Perform the merge that leads to a conflict:
   ```sh
   git merge <conflicting_branch>
   ```
4. Open the conflicting files and decide how to merge the changes.
5. Stage the resolved files:
   ```sh
   git add <resolved_file>
   ```
6. Commit the merge:
   ```sh
   git commit
   ```

---

<div style="width: 100%">
<a href='branching-and-merging.md'><-- Previous Section: Branching and Merging</a>
<div align="right"><a href='resolving-conflicts.md'>Next Section: Resolving Conflicts--></a></div>
</div>
