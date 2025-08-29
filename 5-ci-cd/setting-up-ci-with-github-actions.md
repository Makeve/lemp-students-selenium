# Setting Up CI with GitHub Actions

## Introduction

GitHub Actions allows you to automatically build and run your Selenium tests whenever you push code or create a pull request. This ensures your tests always run in a clean environment without setting up anything locally.

> Tip: YAML is only needed here for GitHub Actions, not Selenium itself.

## 1. Step-by-Step Guide - Using IntelliJ Locally
1. In the Project view, right-click the project root → New → Directory → name it `.github.`
2. Righ-click `.github` → New → Directory → name it `workflows.`
   - Path: `your-project/.github/workflows/`
3. Right-click `workflows` → New → File → name it `ci.yml.`
4. Add your workflow content in `ci.yml.` Example:
 ```yaml

name: Selenium CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      # Step 1: Check out the repository
      - uses: actions/checkout@v4

      # Step 2: Set up Java 17
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'

      # Step 3: Install Chrome
      - name: Install Google Chrome
        run: |
          sudo apt-get update
          sudo apt-get install -y google-chrome-stable

      # Step 4: Build and run tests
      - name: Build and run Selenium tests
        run: mvn clean test


   ```
### 2. Initialize Git locally

1. Go to VCS → Enable Version Control Integration → Git.
2. Git is now initialized in your project.

### 3. Commit your files locally

1. Open the Git panel in IntelliJ or use terminal:
   ```yaml
   git add .
   git commit -m "Initial commit with CI workflow"

   ```
### 4. Create an empty GitHub repository

1. Go to GitHub → New Repository → leave it empty (no README or .gitignore).
2. Copy the repository URL.

### 5. Link local repo to GitHub and push

1. In IntelliJ terminal:
```yaml
git remote add origin https://github.com/your-username/your-repo.git
git branch -M main
git push -u origin main

```
2. Your workflow file (`ci.yml`) is now on GitHub.

### 6. Verify workflow execution

1. Go to your GitHub repo → Actions tab → GitHub automatically detects the workflow.
2. It will run the CI workflow (e.g., Selenium tests) whenever you push new commits.

### 7. Repeat
- Make changes locally → commit → push → GitHub Actions runs → verify results.

 ### 8. Key points to remember:

- YAML file can always be created before Git or GitHub.
- GitHub Actions only triggers once the file is pushed to a GitHub repo.
- Proper YAML indentation is critical — IntelliJ helps with that.

## Step-by-Step Guide - Using GitHub

### 1. Create a `.github/workflows` Directory

1. **Navigate to Your Repository**: Go to your repository on GitHub.
2. **Create a New Directory**: Click on the `Add file` button, then select `Create new file`.
3. **Name the Directory**: In the filename box, type `.github/workflows/` and then add any filename (e.g., `ci.yml`). This will create the necessary directories.
4. **Commit the New File**: Add some content to the file (you can delete it later) and click `Commit new file`.

### 2. Add a ready-to-run workflow

1. **Create a New Workflow File**: If you haven't already, create a new file named `ci.yml` in the `.github/workflows` directory.
2. **Add Workflow Content**: Open the `ci.yml` file and add the following content:
   ```yaml
   name: Selenium CI

   on:
     push:
       branches: [main]
     pull_request:
       branches: [main]

   jobs:
     build:
       runs-on: ubuntu-latest

    steps:
      # Step 1: Check out the repository
      - uses: actions/checkout@v4

      # Step 2: Set up Java 17
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'

      # Step 3: Install Chrome
      - name: Install Google Chrome
        run: |
          sudo apt-get update
          sudo apt-get install -y google-chrome-stable

      # Step 4: Build and run tests
      - name: Build and run Selenium tests
        run: mvn clean test

   ```

### Explanation of steps:

- Checkout code: Gets your repository files into the workflow.
- Set up Java 17: Required for Maven + Selenium.
- Install Chrome: Needed for running Selenium Chrome tests.
- Run tests: Maven builds the project and executes your Selenium tests.
> Tip: Make sure your Selenium code uses WebDriverManager or a similar solution to automatically handle ChromeDriver. Otherwise, tests might fail in GitHub Actions.

### 3. Commit and Push Your Changes

1. **Commit Your Changes**: 
   - Go to the bottom of the `ci.yml` file editor.
   - Add a commit message like "Add GitHub Actions workflow for CI".
   - Click `Commit changes`.

2. **Push Changes to GitHub**: If you are working locally, use the following commands:
   ```sh
   git add .github/workflows/ci.yml
   git commit -m "Add GitHub Actions workflow for Selenium CI"
   git push origin main

   ```
### 4. Verify the Workflow

1. **Check the Actions Tab**: Go to the `Actions` tab in your GitHub repository.
2. **Verify Workflow Execution**: You should see the new workflow running. If everything is set up correctly, it will show a green checkmark indicating that the build passed.
#### If the workflow fails, check the log to see whether it’s a Maven, Java, or ChromeDriver issue.

## Customizing the Workflow

You can customize your GitHub Actions workflow to fit your specific needs. For example, you can add steps for running tests, deploying your application, or building different versions of your application.

## ✅ Summary:

- YAML is only for GitHub Actions.
- Selenium tests don’t require YAML.
- This workflow runs your tests automatically on every push or PR.
- You only need to focus on your Selenium code; CI will handle the rest.

---

<div style="width: 100%">
<a href='introduction-to-ci-cd.md'><-- Previous Section: Introduction to CI/CD Contd.</a>
<div align="right"><a href='running-tests-in-CICD.md'> Next Section: Running Tests in CICD --></a></div>
</div>
