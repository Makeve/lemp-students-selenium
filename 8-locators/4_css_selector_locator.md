# 🎨 Section 4 - CSS Selector Locator  

## 📖 What is a CSS Selector Locator?  

The **CSS Selector locator** uses **CSS selectors** to identify elements on a web page.  

- CSS selectors are very **powerful and flexible**.  
- They allow you to find elements based on:  
  - Attributes  
  - Classes  
  - IDs  
  - Element hierarchy (parent → child relationships)  
- If `id` and `name` are missing, **CSS Selector** is often the best choice.  

👉 Pro Tip: CSS Selectors are widely used in both **web development** and **automation testing**. 

### 🔍 Example: CSS in HTML  

```html
<button class="btn_action">Login</button>
```
- The element above has a class → `"btn_action"`
- We can locate it in Selenium with:
    - By class selector: `.btn_action`
    - By tag + class selector: `button.btn_action`

### Example in Selenium

To locate an element using a CSS selector for the class `btn_action`, you can use the following code:

```java
// Find the element using CSS Selector
WebElement loginButton = driver.findElement(By.cssSelector(".btn_action"));

// Click the button
loginButton.click();
```
### 🎯 Different CSS Selector Patterns
1. By ID
   ```css
   #login-button
    ```
    - Example in Selenium:
      ```java
      driver.findElement(By.cssSelector("#login-button"));
      ```
2. By Class
   ```css
   .btn_action
    ```
    - Example in Selenium:
      ```java
      driver.findElement(By.cssSelector(".btn_action"));
      ```
3. By Attribute
   ```css
   input[name='user-name']
    ```
    - Example in Selenium:
      ```java
      driver.findElement(By.cssSelector("input[name='user-name']"));
      ```
4. By Hierarchy (Parent → Child)
   ```css
   div.login-box input#user-name
    ```
    - Example in Selenium:
      ```java
      driver.findElement(By.cssSelector("div.login-box input#user-name"));
      ```
### 🪜 Steps to Use CSS Selector Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element → and select `Inspect`.
3. **Find the CSS Selector**: Determine the appropriate CSS selector for the element by identifying attributes, classes, or IDs..
4. **Write the Locator in Code**: Use the `By.cssSelector("pattern")` method in your Selenium script to locate the element.

## Practice

Try locating and interacting with different elements on the Sauce Demo website using CSS selectors.  

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Locate the **Username field** → *(Hint: `input[name='user-name']`)*  
- Locate the **Password field** → *(Hint: `input[name='password']`)*  
- Locate the **Login button** → *(Hint: `#login-button`)*  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Enters a username and password  
3. Clicks the login button  

✅ **Rule:** Use **CSS Selectors only**.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoByCssSelector {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Locate elements using CSS Selectors
        WebElement usernameField = driver.findElement(By.cssSelector("input[name='user-name']"));
        WebElement passwordField = driver.findElement(By.cssSelector("input[name='password']"));
        WebElement loginButton = driver.findElement(By.cssSelector("#login-button"));

        // 4. Enter username & password
        usernameField.sendKeys("standard_user");
        passwordField.sendKeys("secret_sauce");

        // 5. Click the login button
        loginButton.click();

        // Optional: close browser
        driver.quit();
    }
}
```
</details>

---

<div style="width: 100%">
<a href='3_classname_locator.md'><-- Previous Section: Class Name Locator</a>
<div align="right"><a href='5_linktext_locator.md'> Next Section: Link Text & Partial Link Text Locator --></a></div>
</div>
