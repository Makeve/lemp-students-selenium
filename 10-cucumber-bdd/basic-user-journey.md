# Basic User Journey Test

In this session, we will learn how to create a basic full user journey test using Cucumber and Selenium. This test will cover a typical user flow in an application, from adding an item to the cart to checking out.

## Step-by-Step Guide

### 1. Create a Feature File (ShoppingJourney.feature)

Create a directory for feature files and add your Gherkin scenarios. For example, create a `ShoppingJourney.feature` file.

```gherkin
Feature: Basic Shopping Journey

  Scenario: Complete user journey from adding an item to checking out
    Given the user is on the home page
    When the user adds an item to the cart
    Then the item should be in the cart
    When the user proceeds to checkout
    Then the user should see the checkout page
    When the user completes the purchase
    Then the user should see a confirmation message
```

### 2. Create Step Definitions (ShoppingJourneySteps.java)

Create step definition classes to map Gherkin steps to Java methods. Inside `src/test/java/stepDefinitions`, create `ShoppingJourneySteps.java`:

```java
package stepDefinitions;

import io.cucumber.java.en.*;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class ShoppingJourneySteps {
    WebDriver driver;

    @Given("the user is on the login page")
    public void userIsOnLoginPage() {
        driver = new ChromeDriver();
        driver.get("https://www.saucedemo.com/");
    }

    @When("the user logs in with valid credentials")
    public void userLogsInWithValidCredentials() {
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();
    }

    @When("the user adds an item to the cart")
    public void userAddsItemToCart() {
        driver.findElement(By.id("add-to-cart-sauce-labs-backpack")).click();
    }

    @Then("the item should be in the cart")
    public void itemShouldBeInCart() {
        driver.findElement(By.className("shopping_cart_link")).click();
        boolean isItemInCart = driver.findElement(By.className("inventory_item_name")).isDisplayed();
        assert isItemInCart;
    }

    @When("the user proceeds to checkout")
    public void userProceedsToCheckout() {
        driver.findElement(By.id("checkout")).click();
    }

    @Then("the user should see the checkout page")
    public void userShouldSeeCheckoutPage() {
        boolean isCheckoutPageDisplayed = driver.findElement(By.id("first-name")).isDisplayed();
        assert isCheckoutPageDisplayed;
    }

    @When("the user completes the purchase")
    public void userCompletesPurchase() {
        driver.findElement(By.id("first-name")).sendKeys("John");
        driver.findElement(By.id("last-name")).sendKeys("Doe");
        driver.findElement(By.id("postal-code")).sendKeys("12345");
        driver.findElement(By.id("continue")).click();
        driver.findElement(By.id("finish")).click();
    }

    @Then("the user should see a confirmation message")
    public void userShouldSeeConfirmationMessage() {
        boolean isConfirmationMessageDisplayed = driver.findElement(By.className("complete-header")).isDisplayed();
        assert isConfirmationMessageDisplayed;
        driver.quit();
    }
}
```

### 3. Create a Test Runner (TestRunner.java)

Create a test runner class to execute your Cucumber tests. Inside `src/test/java`, create `TestRunner.java`:

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

1. **Feature file (.feature)** → Defines the user journey scenario in English (Given-When-Then).
2. **Step Definitions (.java)** → Links each step to actual Selenium code.
3. **Test Runner (.java)** → Executes all feature files.

By following these steps, you can create and run a basic user journey test, ensuring that your application behaves correctly from adding an item to the cart to checking out and receiving a confirmation.

---

<div style="width: 100%">
<a href='running-cucumber-tests.md'><-- Previous Section: Running Cucumber Tests</a>
<div align="right"><a href='../11-final-project/index.md'> Proceed to Week 11 Session: Final Project --></a></div>
</div>
