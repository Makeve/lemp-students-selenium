# Section 4 - CSS Selector Locator

## What is a CSS Selector Locator?

The CSS Selector locator uses CSS selectors to identify elements. It is a powerful and flexible way to locate elements based on their attributes, hierarchy, and other CSS properties.

### Example

To locate an element using a CSS selector for the class `btn_action`, you can use the following code:

```java
WebElement loginButton = driver.findElement(By.cssSelector(".btn_action"));
loginButton.click();
```

### Steps to Use CSS Selector Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the CSS Selector**: Determine the appropriate CSS selector for the element.
4. **Write the Locator**: Use the `By.cssSelector` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using CSS selectors.

---

<div style="width: 100%">
<a href='3_classname_locator.md'><-- Previous Section: Class Name Locator</a>
<div align="right"><a href='5_linktext_locator.md'> Next Section: Link Text & Partial Link Text Locator --></a></div>
</div>
