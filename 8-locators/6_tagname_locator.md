# 🏷️ Section 6 - Tag Name Locator  

## 📖 What is a Tag Name Locator?  

The **Tag Name Locator** uses the **HTML tag name** of an element to find it.  

- Examples of tag names: `<input>`, `<button>`, `<a>`, `<div>`, etc.  
- Since many elements share the same tag, this locator often returns **multiple elements**.  
- Use it when you want to:  
  - Find **all elements of a type** (e.g., all buttons, all links).  
  - Iterate through a list of elements.  

👉 Tag Name locator is rarely used alone, but it’s helpful in finding **lists of elements**.  

### 🔍 Example: Tag in HTML  

```html
<button>Login</button>
<button>Add to Cart</button>
<button>Checkout</button>
```
- All three elements share the same tag → `<button>`
- Using Tag Name locator will return all of them.

### Example in Selenium
To locate all `<button>` elements on a web page, you can use the following code:

```java
// Find all elements with tag <button>
List<WebElement> buttonElements = driver.findElements(By.tagName("button"));

// Loop through and print each button's text
for (WebElement element : buttonElements) {
    System.out.println(element.getText());
}
```

### 🪜 Steps to Use Tag Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element → and select `Inspect`.
3. **Find the Tag Name**: Look at the HTML for the tag, e.g. <button>, <input>, <a>.
4. **Write the Locator in Code**: Use the `By.tagName("tagName")` method in your Selenium script to locate the element.

## Practice

Try locating and interacting with different elements on the Sauce Demo website using their tag names.

👉 **Try this on [Sauce Demo](https://www.saucedemo.com/):**  

- Find all **input fields** → *(Hint: tag = `"input"`)*  
- Find all **buttons** → *(Hint: tag = `"button"`)*  
- Print their text values or send keys to inputs.  

💻 **Your Task:** Write a script that does the following:  
1. Opens Chrome and goes to [Sauce Demo](https://www.saucedemo.com/)  
2. Finds all `<input>` fields and prints how many there are  
3. Finds all `<button>` elements and prints their text values  

✅ **Rule:** Use **Tag Name locator only**.  
## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import java.util.List;

public class SauceDemoByTagName {
    public static void main(String[] args) {
        // 1. Set up ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Open Sauce Demo website
        driver.get("https://www.saucedemo.com/");

        // 3. Find all input fields
        List<WebElement> inputFields = driver.findElements(By.tagName("input"));
        System.out.println("Number of input fields: " + inputFields.size());

        // 4. Find all button elements
        List<WebElement> buttons = driver.findElements(By.tagName("button"));

        // 5. Print the text of each button
        for (WebElement button : buttons) {
            System.out.println("Button text: " + button.getText());
        }

        // Optional: close browser
        driver.quit();
    }
}
```
</details>

<div style="width: 100%">
<a href='5_linktext_locator.md'><-- Previous Section: Link Text & Partial Link Text Locator</a>
<div align="right"><a href='7_xpath_locator.md'> Next Section: XPath Locator --></a></div>
</div>
