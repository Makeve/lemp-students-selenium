# Automated Testing

## Introduction

Automated testing is a crucial part of the CI/CD pipeline. It ensures that your code is tested thoroughly before it is deployed to production. This guide will help you set up automated testing using GitHub Actions.

## Step-by-Step Guide

### 1. Create a Test Suite

1. **Create Test Classes**: Ensure you have a test suite in your project. If you are using Java, you can use JUnit for your tests. Here is an example of a simple test case:
   ```java
   import org.junit.jupiter.api.Test;
   import static org.junit.jupiter.api.Assertions.assertEquals;

   public class ExampleTest {
       @Test
       public void testAddition() {
           assertEquals(2, 1 + 1);
       }
   }
   ```

### 2. Update Your Workflow File

1. **Open Your Workflow File**: Open your existing workflow file (e.g., `ci.yml`) in the `.github/workflows` directory.
2. **Add Test Steps**: Add steps to run your tests. Here is an example for running JUnit tests in a Java project:
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
      - uses: actions/checkout@v4

      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'   # Recommended distribution

      - name: Build with Maven
        run: mvn -B package --file pom.xml
   ```

### 3. Commit and Push Your Changes

1. **Commit Your Changes**:
   - Go to the bottom of the `ci.yml` file editor.
   - Add a commit message like "Add automated tests to GitHub Actions workflow".
   - Click `Commit changes`.

2. **Push Changes to GitHub**: If you are working locally, use the following commands:
   ```sh
   git add .github/workflows/ci.yml
   git commit -m "Add automated tests to GitHub Actions workflow"
   git push origin main
   ```

### 4. Verify the Tests

1. **Check the Actions Tab**: Go to the `Actions` tab in your GitHub repository.
2. **Verify Test Execution**: You should see the workflow running. If everything is set up correctly, it will run your tests and show the results.

## Additional Testing Tools

- **JUnit**: A popular testing framework for Java.
- **Selenium**: A framework for automating web applications for testing purposes.
- **Mockito**: A mocking framework for unit tests in Java.
- **TestNG**: Another testing framework inspired by JUnit.

---

<div style="width: 100%">
<a href='running-tests-in-CICD.md'><-- Previous Section: Running Tests in CICD</a>
<div align="right"><a href='../6-introduction-to-testing/index.md'> Proceed to Week 6 Session: Introduction to Testing --></a></div>
</div>
