# Section 2 - Name Locator

## What is a Name Locator?

The Name locator uses the `name` attribute of an HTML element to identify it. This attribute is not always unique, so it should be used with caution.

### Example

To locate an element with the name `user-name`, you can use the following code:

```java
WebElement usernameField = driver.findElement(By.name("user-name"));
usernameField.sendKeys("standard_user");
```

### Steps to Use Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the Name**: Look for the `name` attribute in the element's HTML code.
4. **Write the Locator**: Use the `By.name` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their names.

---

<div style="width: 100%">
<a href='1_id_locator.md'><-- Previous Section: ID Locator</a>
<div align="right"><a href='3_classname_locator.md'> Next Section: Class Name Locator --></a></div>
</div>
