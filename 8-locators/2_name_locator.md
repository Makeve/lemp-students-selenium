# 🏷️ Section 2 - Name Locator  

## 📖 What is a Name Locator?  

The **Name Locator** uses the **`name` attribute** of an HTML element to find it.  

- Many form fields like username, password, and email often have a `name` attribute.  
- Unlike IDs, the `name` is **not always unique**, so use it with caution.  
- If IDs are missing, `name` is often the **second-best choice**.  

👉 If an element doesn’t have an `id`, check if it has a `name` you can use.  

### 🔍 Example: Name in HTML  

Here’s an example of an input field in HTML:  

```html
<input type="text" name="user-name" />
```
- The element above has a name → `"user-name"`
- Selenium can use this name to locate the input field.

### 💻 Example in Selenium
Here’s how we can type text into the username field using its name:
```java
// Find the element using Name
WebElement usernameField = driver.findElement(By.name("user-name"));

// Type text into the field
usernameField.sendKeys("standard_user");
```

### 🪜 Steps to Use Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element (e.g., Username field) → and select `Inspect`.
3. **Find the Name Attribute**: Look at the HTML in DevTools. Example:
   ```html
   <input type="text" name="user-name" />
    ```
4. **Write the Locator in Your Code**: Use the `By.name("nameValue")` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their names.

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Locate the **Username field** → *(Hint: name = `"user-name"`)*
- Locate the **Password field** → *(Hint: name = `"password"`)*
- Locate the **Login button** *(if it has a name)* and click it  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Enters a username and password  
3. Clicks the Login button  

✅ **Rule:** Use **Name locator only**.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoLoginByName {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Locate elements by Name and interact with them
        WebElement usernameField = driver.findElement(By.name("user-name"));
        WebElement passwordField = driver.findElement(By.name("password"));
        WebElement loginButton = driver.findElement(By.name("login-button")); // if available

        // 4. Enter username & password
        usernameField.sendKeys("standard_user");
        passwordField.sendKeys("secret_sauce");

        // 5. Click the login button
        loginButton.click();

        // Optional: close browser
        driver.quit();
    }
}
</details>
```
---

<div style="width: 100%">
<a href='1_id_locator.md'><-- Previous Section: ID Locator</a>
<div align="right"><a href='3_classname_locator.md'> Next Section: Class Name Locator --></a></div>
</div>
