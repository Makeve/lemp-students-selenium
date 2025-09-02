# Running Tests in CI/CD

## Introduction

In this session, you’ll learn how to automate running your Selenium tests every time you push code or create a pull request, ensuring your tests are always passing without manual intervention.

## Step-by-Step Guide - Advanced Setup (Optional but Useful)

### 1. Verify GitHub Actions Workflow:
- Ensure your `.github/workflows/ci.yml` is set up (from the previous section).
- Make sure `mvn clean test` runs your Selenium tests.

### 2. Upload Test Reports as Artifacts (Optional but useful):
Maven automatically generates XML test reports in `target/surefire-reports/.` You can upload them so they’re downloadable from GitHub Actions. You can generate a test report to check which tests passed or failed. For Maven + TestNG.

Add this code below after your `Run Selenium Tests` step in `ci.yml`:
   ```yaml
        - name: Upload Test Reports
        if: always()   # upload even if tests fail
        uses: actions/upload-artifact@v4
        with:
          name: test-reports
          path: target/surefire-reports/

   ```
📌 This makes XML reports available in the Actions tab as downloadable artifacts.

### 3. Check Results in GitHub Actions:
XML reports are hard to read. Let’s generate HTML reports that open in a browser.
- Go to the Actions tab.
- Open the latest workflow run to see test results.
- Download artifacts if you want detailed reports.
Now in the Actions tab, you’ll see a test-reports artifact you can download.

### 4. Add Surefire HTML Reports (Nicer to Read):
Update your `pom.xml` with this plugin
Add the Surefire Report plugin inside `<build><plugins>`:
```yaml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-surefire-report-plugin</artifactId>
  <version>3.0.0-M9</version>
</plugin>
```
This generates an HTML report at:
`target/site/surefire-report.html`

### 5. Final Example (Full Workflow with Reports):
Here’s the entire yaml file so you can see everything in context:
```yaml
# Name of the workflow (shows up in GitHub Actions tab)
name: Selenium CI

# When the workflow should run
on:
  push:             # Run when code is pushed
    branches: [main]  # Only for the "main" branch
  pull_request:       # Run when a PR is opened/updated
    branches: [main]

jobs:
  # Job name
  build:
    # The environment to run on (Linux with latest Ubuntu)
    runs-on: ubuntu-latest

    steps:
      # Step 1: Checkout (download) the repo code into the runner
      - uses: actions/checkout@v4

      # Step 2: Install Java 17 (required for Maven/Selenium)
      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'   # OpenJDK distribution

      # Step 3: Install Google Chrome (needed for Selenium tests)
      - name: Install Google Chrome
        run: |
          sudo apt-get update
          sudo apt-get install -y google-chrome-stable

      # Step 4: Run tests + generate Surefire HTML report
      - name: Run Tests with Report
        run: mvn clean test surefire-report:report

      # Step 5: Upload the HTML report as an artifact
      # (always uploads, even if tests fail)
      - name: Upload HTML Report
        if: always()
        uses: actions/upload-artifact@v4
        with:
          name: surefire-html                   # artifact name
          path: target/site/surefire-report.html # file to upload
```
### 6. Viewing Reports:
- After the workflow finishes → go to the Actions tab.
- Open the latest run → scroll down to Artifacts.
- Download surefire-html.zip.
- Open surefire-report.html in your browser → you’ll see a clear pass/fail summary for each test.
---

<div style="width: 100%">
<a href='setting-up-ci-with-github-actions.md'><-- Previous Section: Setting up CI with Github Actions</a>
<div align="right"><a href='automated-testing.md'> Next Section: Automated Testing --></a></div>
</div>
