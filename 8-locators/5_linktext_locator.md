# 🔗 Section 5 - Link Text & Partial Link Text Locator  

## 📖 What are Link Text & Partial Link Text Locators?  

The **Link Text** and **Partial Link Text** locators are used to identify **links (`<a>` elements)** on a web page based on the text they display.  

- **Link Text** → matches the **entire text** of a link.  
- **Partial Link Text** → matches a **part of the text** of a link.  

👉 Use these locators when you need to interact with hyperlinks on a page.  

### 🔍 Example: Link in HTML  

```html
<a href="/logout">Logout</a>
```
- Full link text = `"Logout"`
- Partial link text = `"Log"`

### Example in Selenium

To locate a link with the text `Logout`, you can use the following code:

```java
// Locate link by full text
WebElement logoutLink = driver.findElement(By.linkText("Logout"));
logoutLink.click();
```

To locate a link with partial text `Log`, you can use the following code:

```java
// Locate link by partial text
WebElement logoutLinkPartial = driver.findElement(By.partialLinkText("Log"));
logoutLinkPartial.click();
```

### 🪜 Steps to Use Link Text & Partial Link Text Locators

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the link → and select `Inspect`.
3. **Find the Link Text**: Look for the text inside the <a> tag. Example:
   ```html
   <a href="/logout">Logout</a>
   ```
5. **Write the Locator in Your Code**:
   - Use the Full link text: `By.linkText("Logout")`
   - or Partial link text: `By.partialLinkText("Log")` method in your Selenium script to locate the link.

## Practice

Try locating and interacting with different links on the Sauce Demo website using their link text or partial link text. 

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Log in first with your credentials.  
- Locate and click on the **Menu button (☰)** in the top-left corner.  
- Locate the **Logout link** using:  
  - **Full Link Text** → `"Logout"`  
  - **Partial Link Text** → `"Log"`  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Logs in with username and password  
3. Opens the side menu  
4. Clicks the **Logout link** using:  
   - First with **Link Text**  
   - Then with **Partial Link Text**  

✅ **Rule:** Use **Link Text & Partial Link Text locators only**.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoByLinkText {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Log in
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();

        // 4. Open the menu
        driver.findElement(By.id("react-burger-menu-btn")).click();

        // 5. Locate Logout link using full Link Text
        WebElement logoutFull = driver.findElement(By.linkText("Logout"));
        logoutFull.click();

        // (Optional) Re-login to demonstrate Partial Link Text
        driver.get("https://www.saucedemo.com/");
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();
        driver.findElement(By.id("react-burger-menu-btn")).click();

        // 6. Locate Logout link using Partial Link Text
        WebElement logoutPartial = driver.findElement(By.partialLinkText("Log"));
        logoutPartial.click();

        // Optional: close browser
        driver.quit();
    }
}
</details>
```

<div style="width: 100%">
<a href='4_css_selector_locator.md'><-- Previous Section: CSS Selector Locator</a>
<div align="right"><a href='6_tagname_locator.md'> Next Section: Tag Name Locator --></a></div>
</div>
