# Setting Up Cucumber with Selenium

In this session, we will learn how to set up Cucumber with Selenium to automate BDD test cases.

## Step-by-Step Guide

### 1. Update Your `pom.xml`

Make sure your project has the correct dependencies for JUnit 4, Cucumber, and Selenium:

```xml
<dependencies>
    <!-- JUnit (latest JUnit 4 for Cucumber runner) -->
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.13.2</version>
        <scope>test</scope>
    </dependency>

    <!-- Selenium (includes Selenium Manager, no need for drivers path) -->
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.12.1</version>
    </dependency>

    <!-- Cucumber Dependencies -->
    <dependency>
        <groupId>io.cucumber</groupId>
        <artifactId>cucumber-java</artifactId>
        <version>7.15.0</version>
    </dependency>
    <dependency>
        <groupId>io.cucumber</groupId>
        <artifactId>cucumber-junit</artifactId>
        <version>7.15.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>

```

### 2. Create a Feature File (ContactUs.feature)

Create a directory for feature files and add your Gherkin scenarios. For example, Inside `src/test/resources/features,` create `ContactUs.feature:`.

```gherkin
Feature: Contact Us form functionality

  Scenario: Valid Contact Us form submission
    Given User is on the Contact Us page
    When User enters valid details in the form
    And User submits the form
    Then User should see a success message
```

### 3. Create Step Definitions (ContactUsSteps.java)

Create step definition classes to map Gherkin steps to Java methods. Inside `src/test/java/stepDefinitions,` create `ContactUsSteps.java`:

```java
import io.cucumber.java.en.*;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class ContactUsSteps {
    WebDriver driver;

    @Given("User is on the Contact Us page")
    public void userIsOnContactUsPage() {
        driver = new ChromeDriver();
        driver.get("https://example.com/contact-us");
    }

    @When("User enters valid details in the form")
    public void userEntersValidDetails() {
        driver.findElement(By.id("name")).sendKeys("John Doe");
        driver.findElement(By.id("email")).sendKeys("john.doe@example.com");
        driver.findElement(By.id("message")).sendKeys("This is a test message.");
    }

    @And("User submits the form")
    public void userSubmitsTheForm() {
        driver.findElement(By.id("submit")).click();
    }

    @Then("User should see a success message")
    public void userShouldSeeSuccessMessage() {
        boolean isDisplayed = driver.findElement(By.id("successMessage")).isDisplayed();
        assert isDisplayed;
        driver.quit();
    }
}

```

### 4. Create a Test Runner (TestRunner.java)

Create a test runner class to execute your Cucumber tests. Inside `src/test/java,` create `TestRunner.java`:

```java
import org.junit.runner.RunWith;
import io.cucumber.junit.Cucumber;
import io.cucumber.junit.CucumberOptions;

@RunWith(Cucumber.class)
@CucumberOptions(
    features = "src/test/resources/features",
    glue = "stepDefinitions",
    plugin = {"pretty"}
)
public class TestRunner { }

```

## How it Works

1. **Feature file (.feature)** → Defines test scenario in English (Given-When-Then).

2. **Step Definitions (.java)** → Links each step to actual Selenium code.

3. **Test Runner (.java)** → Executes all feature files with JUnit.


### 5. Hands-on Exercise

Task: Write a Cucumber test for login functionality.

Create `Login.feature` in `src/test/resources/features`:

Create `Login.feature` to include:

```gherkin
Feature: Login functionality

  Scenario: Valid user login
    Given User is on the login page
    When User enters valid username and password
    And User clicks the login button
    Then User should be redirected to the dashboard
```

Now create step definitions in `LoginSteps.java` in `src/test/java/stepDefinitions` to handle logging into the application:

💡 Try to write the code yourself first before checking the solution.
<details> 

<summary>💻 Click here to view the solution (hidden)</summary>
    
    ```java
    import io.cucumber.java.en.*;
    import org.openqa.selenium.By;
    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.chrome.ChromeDriver;
    
    public class LoginSteps {
        WebDriver driver;
    
        @Given("User is on the login page")
        public void userIsOnLoginPage() {
            driver = new ChromeDriver();
            driver.get("https://example.com/login");
        }
    
        @When("User enters valid username and password")
        public void userEntersValidCredentials() {
            driver.findElement(By.id("username")).sendKeys("testuser");
            driver.findElement(By.id("password")).sendKeys("password123");
        }
    
        @And("User clicks the login button")
        public void userClicksLoginButton() {
            driver.findElement(By.id("loginButton")).click();
        }
    
        @Then("User should be redirected to the dashboard")
        public void userShouldBeRedirectedToDashboard() {
            boolean isDashboardDisplayed = driver.findElement(By.id("dashboard")).isDisplayed();
            assert isDashboardDisplayed;
            driver.quit();
        }
    }
    ```
</details>

### Step 6: Assignment ✍️

Create a Cucumber test for a user registration scenario.

- **Feature file**: `UserRegistration.feature`
- Steps:
    1. Given the user is on the registration page
    2. When the user enters valid registration details
    3. Then the user should be registered successfully

---

<div style="width: 100%">
<a href='writing-test-cases-in-gherkin-syntax.md'><-- Previous Section: Writing Test Cases in Gherkin Syntax (BDD)</a>
<div align="right"><a href='running-cucumber-tests.md'> Next Section: Running Cucumber Tests --></a></div>
</div>
