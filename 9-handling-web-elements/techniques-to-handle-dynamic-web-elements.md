# Techniques to Handle Dynamic Web Elements

When testing real websites, you’ll often deal with **dynamic elements**.  
These are elements that can **change their properties, location, or state** (enabled/disabled, visible/invisible) depending on user actions or page loading.

👉 Example: On **SauceDemo**, the "Login" button is only useful after you type your username and password. Other elements, like error messages, only appear *after* you try logging in with wrong details.

In this lesson, we’ll learn **how to locate and interact with such elements** safely.

## Step 1: Using Dynamic Locators

Dynamic locators help you find elements that **don’t have fixed attributes** (like ID or Name).  
We often use **XPath** or **CSS Selectors** with partial matches.

### ✅ Example with XPath
```java
// Locate a button using partial text match
WebElement loginBtn = driver.findElement(
    By.xpath("//input[contains(@value,'Login')]")
);
// Click the dynamic element
loginBtn.click();
```

### ✅ Example with CSS Selector
```java
// Locate the login button using part of its class name
WebElement loginBtn = driver.findElement(
    By.cssSelector("input.btn_action")
);
loginBtn.click();

```
## Step 2: Handling Element State Changes

Sometimes elements exist but are not yet clickable (e.g., greyed-out buttons).
In this case, we use Explicit Waits to wait until the element becomes active.
```java
// Wait up to 10 seconds until the Login button is clickable
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement loginBtn = wait.until(
    ExpectedConditions.elementToBeClickable(By.id("login-button"))
);
loginBtn.click();

```
## Step 3: Dealing with Element Visibility

Other times, elements are hidden in the DOM and only become visible later.
We can wait until the element is visible before interacting.

👉 Example: On SauceDemo, error messages only appear after invalid login attempts.
```java
// Wait until the error message is visible after failed login
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement errorMsg = wait.until(
    ExpectedConditions.visibilityOfElementLocated(
        By.cssSelector("h3[data-test='error']")
    )
);
// Print the error message
System.out.println(errorMsg.getText());

```
## 📝 Hands-on Exercise with SauceDemo

👉 Try this on SauceDemo:

1. Open the login page.
2. Enter a wrong username and password.
3. Wait for the error message to appear.
4. Print the text of the error message in the console.

<details>
<summary>💡 Click here to view the solution</summary>
    
```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class DynamicElementHandling {
    public static void main(String[] args) {
        // Launch Chrome
        WebDriver driver = new ChromeDriver();
        
        // Open SauceDemo
        driver.get("https://www.saucedemo.com");

        // Enter invalid username & password
        driver.findElement(By.id("user-name")).sendKeys("wrong_user");
        driver.findElement(By.id("password")).sendKeys("wrong_pass");

        // Click the login button
        driver.findElement(By.id("login-button")).click();

        // Wait for the error message to appear
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
        WebElement errorMsg = wait.until(
            ExpectedConditions.visibilityOfElementLocated(
                By.cssSelector("h3[data-test='error']")
            )
        );

        // Print error text
        System.out.println("Error message: " + errorMsg.getText());

        // Close browser
        driver.quit();
    }
}
```
</details>

## ⚡ Key Takeaways

- Use XPath/CSS for elements with changing attributes.
- Use Explicit Waits when elements take time to load or change state.
- Always wait for elements to be visible or clickable before interacting.
- SauceDemo is a great playground to practice with real dynamic behavior (e.g., error messages, login button, product list).

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Handling Web Elements</a>
<div align="right"><a href='implementing-waits.md'> Next Section: Implementing Waits --></a></div>
</div>
