 # WebDriver Basic Methods

This document provides an overview of some basic methods available in Selenium WebDriver for interacting with web pages.

## Load a New Web Page URL

To load a new web page, use the `get` method:

```java
driver.get("https://www.google.com");
```

## Get the Title of the Current Page

To get the title of the current page, use the `getTitle` method:

```java
String title = driver.getTitle();
System.out.println(title);
```

## Get the URL of the Current Page

To get the URL of the current page, use the `getCurrentUrl` method:

```java
String currentUrl = driver.getCurrentUrl();
System.out.println(currentUrl);
```

## Close the Current Browser Window

To close the current browser window, use the `close` method:

```java
driver.close();
```

## Quit the Driver, Closing ALL Associated Windows

To quit the driver and close all associated windows, use the `quit` method:

```java
driver.quit();
```
-----

<div style="width: 100%">
<a href='first-selenium-script.md'><-- Previous Section: First Selenium Script</a>
<div align="right"><a href='different-browsers.md'> Next Section: Webdriver Different Browsers --></a></div>
</div>
