[Back to Home](../README.md)

# Resolving Conflicts

## Introduction

Merge conflicts occur when Git cannot automatically resolve differences between two commits. This guide will help you understand how to resolve these conflicts.

## Step-by-Step Guide

### Identifying Conflicts

When a conflict occurs, Git will notify you during the merge process. Conflicting files will contain conflict markers (`<<<<<<`, `======`, `>>>>>>`).

### Steps to Resolve Conflicts

1. **Open the Conflicting File**:
   - Look for conflict markers and decide which changes to keep.

2. **Edit the File**:
   - Remove the conflict markers and make necessary edits to resolve the conflict.

3. **Stage the Resolved File**:
   - Once resolved, add the file to the staging area:
   ```sh
   git add <resolved_file>
   ```

4. **Commit the Changes**:
   - Commit the resolved changes:
   ```sh
   git commit
   ```

### Example

#### Steps
1. Create a conflict scenario:
   - Open your terminal.
   - Navigate to your Git repository:
     ```sh
     cd path/to/your/repository
     ```
   - Create a new branch and make changes:
     ```sh
     git checkout -b feature-branch
     echo "Feature change" >> file.txt
     git add file.txt
     git commit -m "Add feature change"
     ```
   - Switch back to the main branch and make conflicting changes:
     ```sh
     git checkout main
     echo "Main change" >> file.txt
     git add file.txt
     git commit -m "Add main change"
     ```
   - Merge the feature branch into the main branch:
     ```sh
     git merge feature-branch
     ```

2. Resolve the conflict:
   - Open the conflicting file (`file.txt`) and look for conflict markers:
     ```
     <<<<<< HEAD
     Main change
     ======
     Feature change
     >>>>>> feature-branch
     ```
   - Edit the file to resolve the conflict:
     ```
     Main change
     Feature change
     ```
   - Stage the resolved file:
     ```sh
     git add file.txt
     ```
   - Commit the resolved changes:
     ```sh
     git commit
     ```

---

<div style="width: 100%">
<a href='branching-and-merging.md'><-- Previous Section: Branching and Merging</a>
<div align="right"><a href='collaborative-workflows.md'>Next Section: Collaborative Workflows--></a></div>
</div>
