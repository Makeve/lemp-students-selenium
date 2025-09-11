# Task: Hands-on Exercise

## Task: Modify the Script to Perform the Following Actions

1. Open the Facebook Login Page
2. Enter email and password
3. Click the Login button
4. Print the error message displayed

### Sample Code:

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqaelenium.chrome.ChromeDriver;

public class FacebookLoginTest {
    public static void main(String[] args) {
        // Set the path to the chromedriver executable
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");

        // Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // Navigate to Facebook login page
        driver.get("https://www.facebook.com/login");

        // Locate the email input field by its ID attribute
        WebElement emailField = driver.findElement(By.id("email"));

        // Locate the password input field by its ID attribute
        WebElement passwordField = driver.findElement(By.id("pass"));

        // Locate the login button by its name attribute
        WebElement loginButton = driver.findElement(By.name("login"));

        // Enter the email
        emailField.sendKeys("your-email@example.com");

        // Enter the password
        passwordField.sendKeys("your-password");

        // Click the login button
        loginButton.click();

        // Locate the error message by its CSS selector or XPath
        WebElement errorMessage = driver.findElement(By.cssSelector("div._9ay7"));

        // Print the error message displayed
        System.out.println("Error Message: " + errorMessage.getText());

        // Close the browser
        driver.quit();
    }
}
```

## Session Summary
- Learned different types of locators.
- Used Chrome DevTools to inspect elements.
- Wrote scripts to interact with text fields, buttons, checkboxes.
- Debugged common errors.

<div style="width: 100%">
<a href='exercise.md'><-- Previous Section: Exercise</a>
<div align="right"><a href='../9-handling-web-elements/index.md'> Proceed to Week 9 Session: Handling Web Elements --></a></div>
</div>
