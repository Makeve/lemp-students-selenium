# 🆔 Section 1 - ID Locator  

## 📖 What is an ID Locator?  

The **ID Locator** uses the **`id` attribute** of an HTML element to find it.  

- Every element on a web page can have an **ID**, and that ID should be **unique**.  
- Because of this, **ID is the most reliable and fastest way** to locate elements in Selenium.  

👉 If you see an element with an `id`, **always prefer using it first**.  

## 🔍 Example: ID in HTML  

Here’s an example of a button in HTML:  

```html
<button id="login-button">Login</button>
```
- The element above has an id → "login-button"
- Selenium can use this id directly to find and interact with it.

### 💻 Example in Selenium

Here’s how we can click the login button using its ID:
```java
// Find the element using ID
WebElement loginButton = driver.findElement(By.id("login-button"));

// Click the button
loginButton.click();

```

### 🪜 Steps to Use ID Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element (e.g., Login button) → and select `Inspect`.
3. **Find the ID Attribute**: Look at the HTML in the DevTools window. Example: <button id="login-button">Login</button>
4. **Write the Locator in Your Code**: Use the `By.id("idValue")` method in your Selenium script to locate the element.

## Practice

Try locating and interacting with different elements on the Sauce Demo website using their IDs.

### 📝 Hands-on Practice  

👉 Try this on [Sauce Demo](https://www.saucedemo.com/):  

- Locate the **Username field** → *(Hint: id = `"user-name"`)*
- Locate the **Password field** → *(Hint: id = `"password"`)*
- Locate the **Login button** → *(Hint: id = `"login-button"`)*  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Enters a username and password  
3. Clicks the Login button  

✅ **Rule:** Use **ID locator only**.  

## ✅ Sample Solution (Java + Selenium)

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoLogin {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver (WebDriverManager can be used in real projects)
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Locate elements by ID and interact with them
        WebElement usernameField = driver.findElement(By.id("user-name"));
        WebElement passwordField = driver.findElement(By.id("password"));
        WebElement loginButton = driver.findElement(By.id("login-button"));

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

<div style="width: 100%">
<a href='introduction.md'><-- Previous Section: Introduction</a>
<div align="right"><a href='2_name_locator.md'> Next Section: Name Locator --></a></div>
</div>
