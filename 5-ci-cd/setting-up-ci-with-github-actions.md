# Setting Up CI with GitHub Actions

## Introduction

GitHub Actions is a powerful CI/CD tool that allows you to automate, customize, and execute your software development workflows right in your GitHub repository. With GitHub Actions, you can build, test, and deploy your code directly from GitHub.

## Step-by-Step Guide

### 1. Create a `.github/workflows` Directory

1. **Navigate to Your Repository**: Go to your repository on GitHub.
2. **Create a New Directory**: Click on the `Add file` button, then select `Create new file`.
3. **Name the Directory**: In the filename box, type `.github/workflows/` and then add any filename (e.g., `ci.yml`). This will create the necessary directories.
4. **Commit the New File**: Add some content to the file (you can delete it later) and click `Commit new file`.

### 2. Create a Workflow File

1. **Create a New Workflow File**: If you haven't already, create a new file named `ci.yml` in the `.github/workflows` directory.
2. **Add Workflow Content**: Open the `ci.yml` file and add the following content:
   ```yaml
   name: CI

   on:
     push:
       branches: [main]
     pull_request:
       branches: [main]

   jobs:
     build:
       runs-on: ubuntu-latest

       steps:
       - uses: actions/checkout@v2
       - name: Set up JDK 11
         uses: actions/setup-java@v2
         with:
           java-version: '11'
       - name: Build with Gradle
         run: ./gradlew build
   ```

### 3. Commit and Push Your Changes

1. **Commit Your Changes**: 
   - Go to the bottom of the `ci.yml` file editor.
   - Add a commit message like "Add GitHub Actions workflow for CI".
   - Click `Commit changes`.

2. **Push Changes to GitHub**: If you are working locally, use the following commands:
   ```sh
   git add .github/workflows/ci.yml
   git commit -m "Add GitHub Actions workflow for CI"
   git push origin main
   ```

### 4. Verify the Workflow

1. **Check the Actions Tab**: Go to the `Actions` tab in your GitHub repository.
2. **Verify Workflow Execution**: You should see the new workflow running. If everything is set up correctly, it will show a green checkmark indicating that the build passed.

## Customizing the Workflow

You can customize your GitHub Actions workflow to fit your specific needs. For example, you can add steps for running tests, deploying your application, or building different versions of your application.

---

<div style="width: 100%">
<a href='introduction-to-ci-cd.md'><-- Previous Section: Introduction to CI/CD Contd.</a>
<div align="right"><a href='deploying-applications.md'> Next Section: Deploying Applications --></a></div>
</div>
