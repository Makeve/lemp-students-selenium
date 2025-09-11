# 🖐️ Hands-on Exercise  

## 📝 Task: Modify the Script to Perform the Following Actions  

1. Open the **Facebook Login Page**  
2. Enter email and password  
3. Click the **Login button**  
4. Print the **error message** displayed  

## ✅ Sample Code (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class FacebookLoginTest {
    public static void main(String[] args) {
        // 1. Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Navigate to Facebook login page
        driver.get("https://www.facebook.com/login");

        // 3. Locate the email input field by its ID attribute
        WebElement emailField = driver.findElement(By.id("email"));

        // 4. Locate the password input field by its ID attribute
        WebElement passwordField = driver.findElement(By.id("pass"));

        // 5. Locate the login button by its name attribute
        WebElement loginButton = driver.findElement(By.name("login"));

        // 6. Enter the email
        emailField.sendKeys("your-email@example.com");

        // 7. Enter the password
        passwordField.sendKeys("your-password");

        // 8. Click the login button
        loginButton.click();

        // 9. Locate the error message by its CSS selector
        WebElement errorMessage = driver.findElement(By.cssSelector("div._9ay7"));

        // 10. Print the error message displayed
        System.out.println("Error Message: " + errorMessage.getText());

        // 11. Close the browser
        driver.quit();
    }
}
```
</details>

## Session Summary
In this lecture, we:
- Learned different types of locators (`id, name, className, cssSelector, linkText, tagName, xpath`).
- Used Chrome DevTools to inspect elements.
- Wrote scripts to interact with **text fields, buttons, links**.
- Practiced debugging common errors when locating elements.

<div style="width: 100%">
<a href='exercise.md'><-- Previous Section: Exercise</a>
<div align="right"><a href='../9-handling-web-elements/index.md'> Proceed to Week 9 Session: Handling Web Elements --></a></div>
</div>
