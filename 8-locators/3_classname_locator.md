# 🏷️ Section 3 - Class Name Locator  

## 📖 What is a Class Name Locator?  

The **Class Name Locator** uses the **`class` attribute** of an HTML element to find it.  

- In HTML, many elements can share the same **class**.  
- A class usually describes the **style or role** of an element (e.g., buttons, containers, menus).  
- Because classes are often reused, **be careful** — it may select multiple elements.  
- If the class name is unique for the element you want, then you can use it.  

👉 Use Class Name locator when `id` and `name` are missing or unreliable.  

### 🔍 Example: Class in HTML  

Here’s an example of an item in HTML:  

```html
<div class="inventory_item">Backpack</div>
```
- The element above has a class → `"inventory_item"`
- Selenium can use this class name to locate the element.

### Example in Selenium

Here’s how we can find and click on an inventory item using its class name:
```java
// Find the element using Class Name
WebElement inventoryItem = driver.findElement(By.className("inventory_item"));

// Click the item
inventoryItem.click();
```
### ⚠️ Important:
If multiple elements share the same class, Selenium will only interact with the first matching element.

### 🪜 Steps to Use Class Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element → and select `Inspect`.
3. **Find the Class Attribute**: Look for the `class` attribute in the element's HTML code. Look in the HTML for something like:
   ```html
   <div class="inventory_item">Backpack</div>
    ```
5. **Write the Locator in Your Code**: Use the `By.className("className")` in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their class names. 

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Locate one of the **product items** → *(Hint: class = `"inventory_item"`)*
- Locate the **shopping cart icon** → *(Hint: class = `"shopping_cart_link"`)*
- Click on the product and then open the shopping cart  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Logs in with username and password  
3. Clicks on one of the products using its class name  
4. Clicks the shopping cart icon (also using its class name)  

✅ **Rule:** Use **Class Name locator only**.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class SauceDemoByClassName {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Log in first
        driver.findElement(By.id("user-name")).sendKeys("standard_user");
        driver.findElement(By.id("password")).sendKeys("secret_sauce");
        driver.findElement(By.id("login-button")).click();

        // 4. Locate a product using class name
        WebElement productItem = driver.findElement(By.className("inventory_item"));
        productItem.click();

        // 5. Locate shopping cart using class name
        WebElement cartIcon = driver.findElement(By.className("shopping_cart_link"));
        cartIcon.click();

        // Optional: close browser
        driver.quit();
    }
}
</details>
```

<div style="width: 100%">
<a href='2_name_locator.md'><-- Previous Section: Name Locator</a>
<div align="right"><a href='4_css_selector_locator.md'> Next Section: CSS Selector Locator --></a></div>
</div>
