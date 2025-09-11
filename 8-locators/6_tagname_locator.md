# Section 6 - Tag Name Locator

## What is a Tag Name Locator?

The Tag Name locator uses the tag name of an HTML element to identify it. This attribute can be shared by multiple elements, so it is often used in combination with other locators.

### Example

To locate all `<button>` elements on a web page, you can use the following code:

```java
List<WebElement> buttonElements = driver.findElements(By.tagName("button"));
for (WebElement element : buttonElements) {
    System.out.println(element.getText());
}
```

### Steps to Use Tag Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the Tag Name**: Identify the tag name of the element.
4. **Write the Locator**: Use the `By.tagName` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their tag names.

---

<div style="width: 100%">
<a href='5_linktext_locator.md'><-- Previous Section: Link Text & Partial Link Text Locator</a>
<div align="right"><a href='7_xpath_locator.md'> Next Section: XPath Locator --></a></div>
</div>
