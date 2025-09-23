# Techniques to Handle Dynamic Web Elements

When testing real websites, you’ll often deal with **dynamic elements**.  
These are elements that can **change their properties, location, or state** (enabled/disabled, visible/invisible) depending on user actions or page loading.

👉 Example: A "Submit" button may only appear after you type in your username and password, or an ad banner may show up randomly on different parts of the page.

In this lesson, we’ll learn **how to locate and interact with such elements** safely.

## 🔑 Step 1: Using Dynamic Locators

Dynamic locators help you find elements that **don’t have fixed attributes** (like ID or Name).  
We often use **XPath** or **CSS Selectors** with partial matches.

### ✅ Example with XPath
```java
// Locate a button using partial text match
WebElement dynamicElement = driver.findElement(
    By.xpath("//button[contains(text(),'Submit')]")
);
// Click the dynamic element
dynamicElement.click();
```

### ✅ Example with CSS Selector
```java
// Locate a button using part of its class name
WebElement dynamicElement = driver.findElement(
    By.cssSelector("button[class*='submit-button']")
);
// Click the dynamic element
dynamicElement.click();
```
## 🔑 Step 2: Handling Element State Changes

Sometimes elements exist but are not yet clickable (e.g., greyed-out buttons).
In this case, we use Explicit Waits to wait until the element becomes active.
```java
// Wait up to 10 seconds until the button is clickable
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement dynamicElement = wait.until(
    ExpectedConditions.elementToBeClickable(By.id("dynamic-button"))
);
dynamicElement.click();
```
## 🔑 Step 3: Dealing with Element Visibility

Other times, elements are hidden in the DOM and only become visible later.
We can wait until the element is visible before interacting.
```java
// Wait until the element is visible before clicking
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
WebElement visibleElement = wait.until(
    ExpectedConditions.visibilityOfElementLocated(By.id("visible-element"))
);
visibleElement.click();
```
## 📝 Hands-on Exercise

👉 Try the following steps on a practice page with dynamic content:

1. Open a webpage with dynamic elements.
2. Locate a dynamic element using XPath or CSS selector.
3. Wait for the element to become clickable.
4. Click the element.

💻 Example Code
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
        
        // Open test site with dynamic elements
        driver.get("https://example.com/dynamic-elements");

        // Wait for max 10 seconds
        WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));

        // Find and click a button that loads dynamically
        WebElement dynamicElement = wait.until(
            ExpectedConditions.elementToBeClickable(
                By.xpath("//button[contains(text(),'Submit')]")
            )
        );
        dynamicElement.click();

        // Close the browser
        driver.quit();
    }
}
```
## ⚡ Key Takeaways

- Use XPath/CSS for elements with changing attributes.
- Use Explicit Waits when elements take time to load or change state.
- Always wait for elements to be visible or clickable before interacting.

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Handling Web Elements</a>
<div align="right"><a href='implementing-waits.md'> Next Section: Implementing Waits --></a></div>
</div>
