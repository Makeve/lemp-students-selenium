# Running Tests in CI/CD

## Introduction

In this session, you’ll learn how to automate running your Selenium tests every time you push code or create a pull request, ensuring your tests are always passing without manual intervention.

## Step-by-Step Guide

### 1. Verify GitHub Actions Workflow:
- Ensure your `.github/workflows/ci.yml` is set up (from the previous section).
- Make sure `mvn clean test` runs your Selenium tests.

### 2. Add Test Reporting (Optional but useful):
You can generate a test report to check which tests passed or failed. For Maven + TestNG:
   ```yaml
  - name: Run Tests
  run: mvn clean test
- name: Upload Test Reports
  uses: actions/upload-artifact@v3
  with:
    name: test-reports
    path: target/surefire-reports/

   ```

### 3. Check Results in GitHub Actions:

- Go to the Actions tab.
- Open the latest workflow run to see test results.
- Download artifacts if you want detailed reports.

---

<div style="width: 100%">
<a href='setting-up-ci-with-github-actions.md'><-- Previous Section: Setting up CI with Github Actions</a>
<div align="right"><a href='automated-testing.md'> Next Section: Automated Testing --></a></div>
</div>
