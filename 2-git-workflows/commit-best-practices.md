[Back to Home](../README.md)

# Commit Best Practices

## Introduction

Writing good commit messages and making atomic commits are essential practices for maintaining a clean and understandable project history.

## Step-by-Step Guide

### Commit Messages

#### Why Good Commit Messages Matter

- **Clarity**: Clearly describe what changes were made and why.
- **History**: Helps understand the project’s evolution.
- **Collaboration**: Makes it easier for collaborators to understand changes.

#### Structure of a Good Commit Message

1. **Title** (50 characters or less):
   - A brief summary of the changes.
   
2. **Body** (optional, 72 characters per line):
   - Detailed explanation of what changes were made and why.

#### Example

```
Add user authentication

Implemented user authentication using JWT. Updated the login and
registration endpoints to generate and validate tokens. Added unit
tests for the authentication service.
```

### Atomic Commits

#### What is an Atomic Commit?

An atomic commit is a single commit that contains related changes. It should do one thing and do it well.

#### Why Atomic Commits Matter

- **Revertability**: Easier to revert specific changes.
- **Reviewability**: Simplifies code reviews.
- **Traceability**: Makes it easier to identify when and why changes were made.

#### How to Make Atomic Commits

1. **Scope Your Changes**: Focus on a single task or feature.
2. **Commit Frequently**: Commit often to avoid large, unwieldy commits.
3. **Test Before Committing**: Ensure your changes work before committing.

#### Example

Instead of this:

```
Add authentication and fix bugs
```

Do this:

1. **Add user authentication**:
   
   ```sh
   git commit -m "Add user authentication"
   ```

2. **Fix bug in user registration**:
   
   ```sh
   git commit -m "Fix bug in user registration"
   ```

---

<div style="width: 100%">
<a href='collaborative-workflows.md'><-- Previous Section: Collaborative Workflows</a>
<div align="right"><a href='../3-project-setup/index.md'>Proceed to WeeK 3 Session: Setting Up Your Project--></a></div>
</div>
