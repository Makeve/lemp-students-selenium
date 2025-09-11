# Section 1 - ID Locator

## What is an ID Locator?

The ID locator uses the `id` attribute of an HTML element to identify it. IDs are unique within a web page, making them the most reliable way to locate elements.

### Example

To locate an element with the ID `login-button`, you can use the following code:

```java
WebElement loginButton = driver.findElement(By.id("login-button"));
loginButton.click();
```

### Steps to Use ID Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the ID**: Look for the `id` attribute in the element's HTML code.
4. **Write the Locator**: Use the `By.id` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their IDs.

---

<div style="width: 100%">
<a href='introduction.md'><-- Previous Section: Introduction</a>
<div align="right"><a href='2_name_locator.md'> Next Section: Name Locator --></a></div>
</div>
