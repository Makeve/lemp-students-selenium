# Section 7 - XPath Locator

## What is an XPath Locator?

The XPath locator uses XPath expressions to identify elements. It is a powerful and flexible way to locate elements based on their attributes, hierarchy, and other properties.

### Example

To locate an element using an XPath expression for a button with the text `Login`, you can use the following code:

```java
WebElement loginButton = driver.findElement(By.xpath("//button[text()='Login']"));
loginButton.click();
```

### Steps to Use XPath Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the XPath**: Determine the appropriate XPath expression for the element.
4. **Write the Locator**: Use the `By.xpath` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using XPath expressions.

---

<div style="width: 100%">
<a href='6_tagname_locator.md'><-- Previous Section: Tag Name Locator</a>
<div align="right"><a href='exercise.md'> Next Section: Exercise --></a></div>
</div>
