# Section 5 - Link Text & Partial Link Text Locator

## What are Link Text & Partial Link Text Locators?

Link Text and Partial Link Text locators are used to identify links on a web page based on their text. The Link Text locator uses the entire text of the link, while the Partial Link Text locator uses a portion of the link text.

### Example

To locate a link with the text `Logout`, you can use the following code:

```java
WebElement logoutLink = driver.findElement(By.linkText("Logout"));
logoutLink.click();
```

To locate a link with partial text `Log`, you can use the following code:

```java
WebElement logoutLinkPartial = driver.findElement(By.partialLinkText("Log"));
logoutLinkPartial.click();
```

### Steps to Use Link Text & Partial Link Text Locators

1. **Open the Web Page**: Navigate to the [Sauce Demo](https://www.saucedemo.com/) website.
2. **Inspect the Element**: Right-click on the link and select `Inspect`.
3. **Find the Link Text**: Identify the text of the link.
4. **Write the Locator**: Use the `By.linkText` or `By.partialLinkText` method in your Selenium script to locate the link.

### Practice

Try locating and interacting with different links on the Sauce Demo website using their link text or partial link text.

---

<div style="width: 100%">
<a href='4_css_selector_locator.md'><-- Previous Section: CSS Selector Locator</a>
<div align="right"><a href='6_tagname_locator.md'> Next Section: Tag Name Locator --></a></div>
</div>
