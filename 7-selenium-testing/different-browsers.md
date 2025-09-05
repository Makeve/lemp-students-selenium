# WebDriver Different Browsers

## Introduction

Selenium WebDriver supports multiple browsers, allowing you to execute your tests across different environments. This guide will walk you through setting up WebDriver for Firefox, Microsoft Edge, and Safari.

### Firefox Driver

To execute tests in Firefox, you need to download and use the **geckodriver**. Follow these steps:

1. **Download geckodriver**:
   - Go to the [geckodriver releases page](https://github.com/mozilla/geckodriver/releases).
   - Download the latest version compatible with your operating system.
   - Extract the downloaded file to a location on your system (e.g., `C:\drivers\geckodriver.exe` on Windows or `/usr/local/bin/geckodriver` on macOS/Linux).

2. **Set System Property for geckodriver**:
   - As per Selenium requirements, set the `webdriver.gecko.driver` property.

```java
System.setProperty("webdriver.gecko.driver", "C:\\drivers\\geckodriver.exe");
```

3. **Create WebDriver Object for Firefox**:
   - Create an instance of `FirefoxDriver`.

```java
WebDriver driver = new FirefoxDriver();
```

4. **Execute Your Test**:
   - During test execution, the steps will be performed on the Firefox browser.

### Microsoft Edge Driver

To execute tests in Microsoft Edge, you need to download and use the **EdgeDriver**. Follow these steps:

1. **Check Your Microsoft Edge Version**:
   - Open Microsoft Edge.
   - Navigate to: `3 Dots Menu > Help and feedback > About Microsoft Edge`.
   - Note the version number.

2. **Download EdgeDriver**:
   - Go to the [Microsoft Edge Driver page](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/).
   - Download the version of EdgeDriver that matches your Microsoft Edge version.
   - Extract the downloaded file to a location on your system (e.g., `C:\drivers\msedgedriver.exe`).

3. **Set System Property for EdgeDriver**:
   - As per Selenium requirements, set the `webdriver.edge.driver` property.

```java
System.setProperty("webdriver.edge.driver", "C:\\drivers\\msedgedriver.exe");
```

4. **Create WebDriver Object for Edge**:
   - Create an instance of `EdgeDriver`.

```java
WebDriver driver = new EdgeDriver();
```

5. **Execute Your Test**:
   - During test execution, the steps will be performed on the Microsoft Edge browser.

### Safari Driver

To execute tests in Safari, you need to use the **SafariDriver**. Follow these steps:

1. **Enable Remote Automation**:
   - Open Safari.
   - Go to `Safari > Preferences > Advanced`.
   - Check the box for `Show Develop menu in menu bar`.
   - Go to `Develop > Allow Remote Automation`.

2. **Set System Property for SafariDriver**:
   - SafariDriver does not require setting a system property, but you must ensure that the Safari browser is configured to allow remote automation.

3. **Create WebDriver Object for Safari**:
   - Create an instance of `SafariDriver`.

```java
WebDriver driver = new SafariDriver();
```

4. **Execute Your Test**:
   - During test execution, the steps will be performed on the Safari browser.

### Summary

By following the steps outlined above, you can configure Selenium WebDriver to execute tests across different browsers, ensuring comprehensive cross-browser testing.

---

<div style="width: 100%">
<a href='first-selenium-script.md'><-- Previous Section: First Selenium Scripts</a>
<div align="right"><a href='../8-locators/index.md'> Proceed to Week 8 Session: Locators --></a></div>
</div>
