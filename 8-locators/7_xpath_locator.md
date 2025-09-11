# 🧭 Section 7 - XPath Locator  

## 📖 What is an XPath Locator?  

The **XPath Locator** uses **XPath expressions** to find elements on a web page.  

- XPath stands for **XML Path Language**.  
- It is very **powerful and flexible**.  
- With XPath, you can locate elements by:  
  - Tag names  
  - Attributes  
  - Text content  
  - Parent-child hierarchy  

👉 XPath is often used when elements **don’t have unique IDs or names**.  

## 🔍 Example: XPath in HTML  

```html
<button id="login-button">Login</button>
```
Using XPath:
  - By tag + attribute:
    ```xpath
    //button[@id='login-button']
    ```
  - By text:
    ```xpath
    //button[text()='Login']
    ```
### Example in Selenium

To locate an element using an XPath expression for a button with the text `Login`, you can use the following code:

```java
// Locate by attribute
WebElement loginButton = driver.findElement(By.xpath("//button[@id='login-button']"));
loginButton.click();

// Locate by text
WebElement loginButtonText = driver.findElement(By.xpath("//button[text()='Login']"));
loginButtonText.click();
```
### 🎯 Types of XPath
1. Absolute XPath
  - Starts from the root `(html)` and goes down step by step.
  - Example:
    ```xpath
    /html/body/div/div/form/input
    ```
⚠️ Not recommended (too fragile — breaks if page structure changes).

2. Relative XPath
  - Starts with `//` and finds elements anywhere in the page.
  - Example:
    ```xpath
    //input[@id='user-name']
    ```
✔️ Preferred because it’s more flexible.

3. Advanced XPath Examples
  - Using multiple attributes:
    ```xpath
    //input[@id='user-name' and @type='text']
    ```
  - Contains (partial match):
    ```xpath
    //button[contains(text(),'Log')]
    ```
  - Starts-with:
    ```xpath
    //input[starts-with(@id,'user')]
    ```
  - Parent → Child:
    ```xpath
    //div[@class='login-box']//input[@id='password']
    ```
### 🪜 Steps to Use XPath Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element → and select `Inspect`.
3. **Find the XPath**: Determine the appropriate XPath expression for the element by Identifying attributes, text, or hierarchy.
4. **Write the Locator in Code**: Use the `By.xpath("expression")` method in your Selenium script to locate the element.

## Practice

Try locating and interacting with different elements on the Sauce Demo website using XPath expressions. 

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Locate the **Username field** → *(Hint: `//input[@id='user-name']`)*  
- Locate the **Password field** → *(Hint: `//input[@id='password']`)*  
- Locate the **Login button** → *(Hint: `//input[@id='login-button']`)*  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Enters a username and password using XPath locators  
3. Clicks the login button  

✅ **Rule:** Use **XPath locators only**.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoByXPath {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Locate elements using XPath
        WebElement usernameField = driver.findElement(By.xpath("//input[@id='user-name']"));
        WebElement passwordField = driver.findElement(By.xpath("//input[@id='password']"));
        WebElement loginButton = driver.findElement(By.xpath("//input[@id='login-button']"));

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
<a href='6_tagname_locator.md'><-- Previous Section: Tag Name Locator</a>
<div align="right"><a href='exercise.md'> Next Section: Exercise --></a></div>
</div>
