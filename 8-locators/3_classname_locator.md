# Section 3 - Class Name Locator

## What is a Class Name Locator?

The Class Name locator uses the `class` attribute of an HTML element to identify it. This attribute can be shared by multiple elements, so it's essential to ensure it uniquely identifies the element you want.

### Example

To locate an element with the class name `inventory_item`, you can use the following code:

```java
WebElement inventoryItem = driver.findElement(By.className("inventory_item"));
inventoryItem.click();
```

### Steps to Use Class Name Locator

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the element and select `Inspect`.
3. **Find the Class Name**: Look for the `class` attribute in the element's HTML code.
4. **Write the Locator**: Use the `By.className` method in your Selenium script to locate the element.

### Practice

Try locating and interacting with different elements on the Sauce Demo website using their class names.

---

<div style="width: 100%">
<a href='2_name_locator.md'><-- Previous Section: Name Locator</a>
<div align="right"><a href='4_css_selector_locator.md'> Next Section: CSS Selector Locator --></a></div>
</div>
