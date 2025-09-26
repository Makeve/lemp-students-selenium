# Implementing Waits (Implicit, Explicit, and Fluent Waits)

In the previous lesson, we learned how to handle **dynamic elements** — elements that change their attributes, visibility, or state.  

But there’s another challenge in real websites: **timing**.  
Even if you know how to locate an element, it may not be ready immediately.  
It might take a few seconds to appear, become clickable, or load fully.

👉 Example: On [SauceDemo](https://www.saucedemo.com), after logging in, the **Products page title** or the **cart icon** doesn’t always appear instantly.  

⚡ **This lesson builds on dynamic elements** and teaches you how to:  
- Apply **implicit waits** (for all elements).  
- Use **explicit waits** (for specific conditions).  
- Implement **fluent waits** (for advanced polling and control).  

Think of it as the missing piece:  
- Dynamic locators = *finding the right element*.  
- Waits = *waiting until the element is ready*.

## ⏳ 1. Implicit Waits

An **implicit wait** tells Selenium to **keep trying to find an element** for a set time before throwing an error.  
It applies to **all elements** in your test.

### ✅ Example
```java
WebDriver driver = new ChromeDriver();

// Set a global implicit wait of 10 seconds
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

// Open SauceDemo
driver.get("https://www.saucedemo.com");

// Locate elements (Selenium will wait up to 10 seconds if needed)
driver.findElement(By.id("user-name")).sendKeys("standard_user");
driver.findElement(By.id("password")).sendKeys("secret_sauce");
driver.findElement(By.id("login-button")).click();
```
## ⏳ 2. Explicit Waits

An explicit wait is smarter.
It waits until a specific condition is met (e.g., an element is visible, clickable, or contains text).

✅ Example
```java
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

// Wait until the Products page title is visible after login
WebElement productsTitle = wait.until(
    ExpectedConditions.visibilityOfElementLocated(By.className("title"))
);

System.out.println("Page Title: " + productsTitle.getText());
```
## ⏳ 3. Fluent Waits

A fluent wait gives you more control:

- Maximum time to wait
- How often to check (polling interval)
- Ignore exceptions while waiting

✅ Example
```java
Wait<WebDriver> fluentWait = new FluentWait<>(driver)
    .withTimeout(Duration.ofSeconds(30))     // total wait time
    .pollingEvery(Duration.ofSeconds(5))     // check every 5 seconds
    .ignoring(NoSuchElementException.class); // ignore errors while waiting

// Wait until the shopping cart icon is present
WebElement cartIcon = fluentWait.until(driver ->
    driver.findElement(By.className("shopping_cart_link"))
);

cartIcon.click();
```
## 📝 Hands-on Exercise with SauceDemo

👉 Your Task:

1. Open [SauceDemo](https://www.saucedemo.com/)
2. Apply an implicit wait of 10 seconds.
3. Log in with credentials:
     - Username: standard_user
     - Password: secret_sauce
4. Use an explicit wait to confirm that the Products page has loaded.
5. Use a fluent wait to find and click the shopping cart icon.

<details> 
  <summary>💡 Click here to reveal the solution</summary>
  
  ```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.FluentWait;
import org.openqa.selenium.support.ui.Wait;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.time.Duration;
import java.util.NoSuchElementException;

public class WaitsDemo {
    public static void main(String[] args) {
        // Launch Chrome
        WebDriver driver = new ChromeDriver();

        // Set implicit wait
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));

        // Open SauceDemo
        driver.get("https://www.saucedemo.com");

        // Login
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();

        // Explicit wait for Products page
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
        WebElement productsTitle = wait.until(
            ExpectedConditions.visibilityOfElementLocated(By.className("title"))
        );
        System.out.println("Page loaded: " + productsTitle.getText());

        // Fluent wait for shopping cart
        Wait<WebDriver> fluentWait = new FluentWait<>(driver)
            .withTimeout(Duration.ofSeconds(20))
            .pollingEvery(Duration.ofSeconds(2))
            .ignoring(NoSuchElementException.class);

        WebElement cartIcon = fluentWait.until(d ->
            d.findElement(By.className("shopping_cart_link"))
        );
        cartIcon.click();

        // Close browser
        driver.quit();
    }
}
```
</details>

## ⚡ Key Takeaways

- Implicit Wait → applies to all elements, simple but less flexible.
- Explicit Wait → waits for specific conditions (best practice).
- Fluent Wait → advanced control over polling and ignored exceptions.

Using waits wisely prevents flaky tests and makes your automation much more stable.

<div style="width: 100%">
<a href='techniques-to-handle-dynamic-web-elements.md'><-- Previous Section: Techniques to Handle Dynamic Web Elements</a>
<div align="right"><a href='../10-cucumber-bdd/index.md'> Proceed to Week 10 Session: Introduction to Cucumber for BDD --></a></div>
</div>
