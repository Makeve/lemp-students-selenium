# Running Cucumber Tests

In this session, we will learn how to run Cucumber tests and understand the results. Running Cucumber tests involves executing the feature files you've created and reviewing the output to ensure that your application behaves as expected.

## Step-by-Step Guide

### 1. Setting Up the Environment

Before running Cucumber tests, ensure you have set up your environment correctly. This includes having the necessary dependencies in your `pom.xml` file and the feature files and step definitions in place.

### 2. Running Tests Using Maven

If you are using Maven, you can run your Cucumber tests using the following command:

```sh
mvn test
```

This command will execute all the tests in your project, including the Cucumber tests.

### 3. Running Tests Using JUnit

If you prefer to run tests using JUnit, you can do so by running the TestRunner class. Ensure your TestRunner class is set up as follows:

```java
import org.junit.runner.RunWith;
import io.cucumber.junit.Cucumber;
import io.cucumber.junit.CucumberOptions;

@RunWith(Cucumber.class)
@CucumberOptions(features="src/test/resources/features", glue="stepDefinitions")
public class TestRunner { }
```

You can run this class directly from your IDE, or by using the following Maven command:

```sh
mvn -Dtest=TestRunner test
```

### 4. Reviewing Test Results

After running the tests, you will see the output in the console. The output will show which scenarios passed and which failed. Here's an example of what the output might look like:

```
Feature: User login functionality

  Scenario: Successful login with valid credentials
    Given the user is on the login page
    When the user enters valid credentials
    Then the user should be redirected to the dashboard

1 Scenarios (1 passed)
3 Steps (3 passed)
0m1.234s
```

### 5. Interpreting the Results

- **Feature**: This section shows the feature being tested.
- **Scenario**: This section shows the specific scenario being tested.
- **Steps**: This section shows the steps in the scenario and whether they passed or failed.
- **Summary**: This section provides a summary of the number of scenarios and steps that passed or failed, along with the total execution time.

### 6. Handling Test Failures

If a test fails, the output will provide details about the failure, including the step that failed and the reason for the failure. Here's an example of a failure message:

```
Feature: User login functionality

  Scenario: Successful login with valid credentials
    Given the user is on the login page
    When the user enters valid credentials
    Then the user should be redirected to the dashboard

1 Scenarios (1 failed)
3 Steps (2 passed, 1 failed)
0m1.234s

java.lang.AssertionError: expected:<true> but was:<false>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertTrue(Assert.java:41)
	at stepDefinitions.LoginSteps.userShouldBeRedirectedToDashboard(LoginSteps.java:25)
```

In this example, the test failed because the expected condition (`true`) did not match the actual condition (`false`). The error message also shows the line number in the step definition where the failure occurred.

### 7. Debugging and Fixing Failures

To debug and fix test failures, follow these steps:

1. **Identify the failing step**: Look at the error message to identify which step failed.
2. **Check the step definition**: Review the step definition code to understand why the step failed.
3. **Fix the issue**: Make the necessary changes to the step definition or application code to fix the issue.
4. **Re-run the tests**: After making the changes, re-run the tests to ensure the issue is resolved.

### Additional Tips

- **Use meaningful names**: Ensure your feature and scenario names are descriptive and meaningful.
- **Keep scenarios focused**: Each scenario should test a single behavior or interaction.
- **Review results regularly**: Regularly review the test results to ensure your application continues to behave as expected.

By following these steps, you can effectively run and manage your Cucumber tests, ensuring your application meets the desired behavior and quality standards.

---

<div style="width: 100%">
<a href='setting-up-cucumber-with-selenium.md'><-- Previous Section: Setting Up Cucumber with Selenium</a>
<div align="right"><a href='basic-user-journey.md'> Next Section: Basic User Journey --></a></div>
</div>
