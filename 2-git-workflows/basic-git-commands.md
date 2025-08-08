[Back to Home](../README.md)

# Basic Git Commands

## Introduction

This guide covers the basic Git commands you'll use frequently. These commands will help you manage your code and collaborate with others effectively.

## Step-by-Step Guide

### 1. `git init`

Initializes a new Git repository in your project directory.

#### Steps
1. Open your terminal.
2. Navigate to your project directory:
   ```sh
   cd path/to/your/project
   ```
3. Initialize the Git repository:
   ```sh
   git init
   ```

### 2. `git clone`

Clones an existing repository into a new directory.

#### Steps
1. Open your terminal.
2. Navigate to the directory where you want to clone the repository:
   ```sh
   cd path/to/desired/directory
   ```
3. Clone the repository:
   ```sh
   git clone <repository_url>
   ```

### 3. `git status`

Displays the state of the working directory and staging area.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Check the status:
   ```sh
   git status
   ```

### 4. `git add`

Adds changes in the working directory to the staging area.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Add a specific file:
   ```sh
   git add <file_name>
   ```
   Or add all changes:
   ```sh
   git add .
   ```

### 5. `git commit`

Records changes to the repository.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Commit the changes with a message:
   ```sh
   git commit -m "Your commit message"
   ```

### 6. `git push`

Uploads local repository content to a remote repository.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Push the changes:
   ```sh
   git push <remote_name> <branch_name>
   ```

### 7. `git pull`

Fetches and integrates changes from a remote repository to the local repository.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Pull the changes:
   ```sh
   git pull <remote_name> <branch_name>
   ```

### 8. `git log`

Shows the commit history for the current branch.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. View the commit history:
   ```sh
   git log
   ```

### 9. `git diff`

Shows the differences between the working directory and the staging area.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. View the differences:
   ```sh
   git diff
   ```

### 10. `git branch`

Lists all branches in the local repository.

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

### 11. `git checkout`

Switches to a different branch or restores working directory files.

#### Steps
1. Open your terminal.
2. Navigate to your Git repository:
   ```sh
   cd path/to/your/repository
   ```
3. Switch to a specific branch:
   ```sh
   git checkout <branch_name>
   ```
4. Create and switch to a new branch:
   ```sh
   git checkout -b <new_branch_name>
   ```

### 12. `git merge`

Merges changes from one branch into another.

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

---

<div style="width: 100%">
<a href='introduction.md'><-- Previous Section: Introduction</a>
<div align="right"><a href='branching-and-merging.md'>Next Section: Branching and Merging--></a></div>
</div>
