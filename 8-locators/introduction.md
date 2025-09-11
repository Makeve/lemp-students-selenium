# 🔍 Introduction to Locators  

## 📖 What are Locators?  

Locators are **identifiers** that help Selenium find and interact with elements on a web page.  

👉 Think of locators like an **address system**:  
- Just like you need an address to find a house,  
- Selenium needs a **locator** to find elements such as buttons, text boxes, and links.  

Once an element is found, Selenium can **click**, **type text**, **select checkboxes**, or **interact** in many other ways.  

## 💡 Why are Locators Important?  

- ✅ **Uniquely identify elements** on a web page  
- ✅ **Enable interactions** → clicking buttons, typing in fields, selecting checkboxes, etc.  
- ✅ **Improve test stability & accuracy** → reliable tests depend on accurate locators  

## 🧩 Types of Locators in Selenium  

Here are the most commonly used locator strategies in Selenium:  

| Locator Type       | Example                          | Best For / Use Case |
|--------------------|----------------------------------|---------------------|
| **ID**             | `By.id("username")`             | Fastest & most reliable. Use when element has a unique ID. |
| **Name**           | `By.name("email")`              | Use when ID isn’t available. Second fastest. |
| **Class Name**     | `By.className("input-field")`   | Works if class name is unique. |
| **CSS Selector**   | `By.cssSelector("#login-btn")`  | Very flexible. Good fallback when ID/Name aren’t available. |
| **Link Text**      | `By.linkText("Forgot Password")`| Use for links (`<a>` tags) with unique visible text. |
| **Partial Link Text** | `By.partialLinkText("Forgot")` | Useful if link text is long, or only part of it is unique. |
| **Tag Name**       | `By.tagName("input")`           | Use for elements where the tag is unique. |
| **XPath**          | `By.xpath("//div[@id='submit']")` | Most powerful & flexible, but can be slower and harder to maintain. |
| **DOM** (JavaScript) | `document.getElementById("exampleId")` | Rarely used in Selenium directly, but useful for debugging in DevTools. |

⚡ **Best Practice**: Always try **ID** first → then **Name** → then CSS/XPath as fallback.  

## 📌 Why Choosing the Right Locator Matters  

- 🚀 **Speed** → IDs and Names are fastest.  
- 🎯 **Accuracy** → A correct locator ensures Selenium interacts with the right element.  
- 🔒 **Reliability** → Poor locator strategies lead to flaky tests.  

## 🌍 Practice Website  

For this session, we’ll use:  
👉 [Sauce Demo](https://www.saucedemo.com/)  

Browser: **Google Chrome**  

---

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Locators</a>
<div align="right"><a href='1_id_locator.md'> Next Section: ID Locator --></a></div>
</div>
