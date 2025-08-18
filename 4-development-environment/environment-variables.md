# Environment Variables

## Introduction

Environment variables are key-value pairs that can be used to configure the behavior of applications and development environments. This guide will help you set up and manage environment variables in your development environment.

## Step-by-Step Guide

### 1. Setting Environment Variables in IntelliJ IDEA

1. **Open Run/Debug Configurations**:
   - Open IntelliJ IDEA.
   - Go to `Run` > `Edit Configurations`.

2. **Select a Configuration**:
   - Select the configuration for which you want to set environment variables.

3. **Edit Environment Variables**:
   - In the `Configuration` pane, look for the `Environment variables` field.
   - Click the `...` button to open the `Environment Variables` dialog.
   - Add, edit, or remove environment variables as needed.
   - Click `OK` to save your changes.

### 2. Setting Environment Variables in the Terminal

#### macOS and Linux

1. **Open Terminal**: Open your terminal.

2. **Set Environment Variable Temporarily**:
   ```sh
   export VARIABLE_NAME=value
   ```

3. **Set Environment Variable Permanently**:
   - Open your shell configuration file (e.g., `.bashrc`, `.zshrc`):
     ```sh
     nano ~/.bashrc
     ```
   - Add the following line:
     ```sh
     export VARIABLE_NAME=value
     ```
   - Save and close the file.
   - Apply the changes:
     ```sh
     source ~/.bashrc
     ```

#### Windows

1. **Open Environment Variables**:
   - Right-click on `This PC` or `Computer` on the desktop and select `Properties`.
   - Click on `Advanced system settings`.
   - Click on the `Environment Variables` button.

2. **Set Environment Variable**:
   - In the `System Properties` window, click on `New` under `User variables` or `System variables`.
   - Enter the `Variable name` and `Variable value`.
   - Click `OK` to save the changes.

### 3. Using Environment Variables in Code

#### Java

1. **Access Environment Variables**:
   ```java
   String value = System.getenv("VARIABLE_NAME");
   ```

#### JavaScript (Node.js)

1. **Access Environment Variables**:
   ```javascript
   const value = process.env.VARIABLE_NAME;
   ```

---

<div style="width: 100%">
<a href='useful-plugins.md'><-- Previous Section: Useful Plugins</a>
<div align="right"><a href='build-tools.md'>Next Section: Build Tools--></a></div>
</div>
