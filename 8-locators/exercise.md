# Selenium Exercise: Writing Scripts to Interact with Web Elements

## Exercise 1: Writing Selenium Scripts to Interact with Web Elements

### Test Case: Search in Google

In this exercise, you will write a Selenium script to perform a search on Google.

#### Steps:
1. Open a web browser and navigate to https://www.google.com.
2. Locate the search input field using its name attribute.
3. Enter the search term "Selenium WebDriver" into the search input field.
4. Submit the search form.
5. Verify that the search results page is displayed.

#### Sample Code:

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class GoogleSearchTest {
    public static void main(String[] args) {
        // Set the path to the chromedriver executable
        System.setProperty("webdriver.chrome.driver", "C://Users//YourName//chromedriver.exe");

        // Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to Google
        driver.get("https://www.google.com");

        // Locate the search input field by its name attribute
        WebElement searchField = driver.findElement(By.name("q"));

        // Enter the search term
        searchField.sendKeys("Selenium WebDriver");

        // Submit the search form
        searchField.submit();

        // Verify that the search results page is displayed
        String title = driver.getTitle();
        if (title.contains("Selenium WebDriver")) {
            System.out.println("Test Passed");
        } else {
            System.out.println("Test Failed");
        }

        // Close the browser
        driver.quit();
    }
}
```

## Exercise 2: Interacting with Buttons, Checkboxes & Radio Buttons

### Test Case: Login Form Automation

In this exercise, you will write a Selenium script to automate a login form.

#### Steps:
1. Open a web browser and navigate to the login page.
2. Locate the username input field using its ID attribute.
3. Locate the password input field using its ID attribute.
4. Locate the login button using its name attribute.
5. Enter the username and password.
6. Click the login button.
7. Verify that the login was successful by checking the presence of a specific element.

#### Sample Code:

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginFormTest {
    public static void main(String[] args) {
        // Set the path to the chromedriver executable
        System.setProperty("webdriver.chrome.driver", "C://Users//YourName//chromedriver.exe");

        // Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to the login page
        driver.get("https://example.com/login");

        // Locate the username input field by its ID attribute
        WebElement usernameField = driver.findElement(By.id("username"));

        // Locate the password input field by its ID attribute
        WebElement passwordField = driver.findElement(By.id("password"));

        // Locate the login button by its name attribute
        WebElement loginButton = driver.findElement(By.name("login"));

        // Enter the username
        usernameField.sendKeys("your-username");

        // Enter the password
        passwordField.sendKeys("your-password");

        // Click the login button
        loginButton.click();

        // Verify that the login was successful by checking the presence of a specific element
        WebElement dashboardElement = driver.findElement(By.id("dashboard"));
        if (dashboardElement.isDisplayed()) {
            System.out.println("Login Test Passed");
        } else {
            System.out.println("Login Test Failed");
        }

        // Close the browser
        driver.quit();
    }
}
```

Practice these exercises to become proficient in writing Selenium scripts to interact with various web elements.

<div style="width: 100%">
<a href='7_xpath_locator.md'><-- Previous Section: Xpath Locator</a>
<div align="right"><a href='hands-on-exercise.md'> Next Section: Hands-on Exercise --></a></div>
</div>
