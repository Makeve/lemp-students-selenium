# Writing Your First Test

## Introduction

In this guide, we will write your **first Selenium test** in Java.  
The test will open a website, interact with a web element, and verify the page title.  

> **Note:** If you are using Maven with Selenium 4.6 or newer, **Selenium Manager** automatically handles the browser driver, so you do **not** need to set `webdriver.chrome.driver` manually.

## Step-by-Step Guide

### 1. Create a New Test Class

1. **Create a New Java Class**:
   - Open your IDE (e.g., IntelliJ IDEA, Eclipse).
   - Create a new Java class named `FirstSeleniumTest`.

### 2. Import Selenium Libraries

1. **Add Import Statements**:
   - Add the necessary import statements to your class.
   ```java
   import org.openqa.selenium.By;
   import org.openqa.selenium.WebDriver;
   import org.openqa.selenium.WebElement;
   import org.openqa.selenium.chrome.ChromeDriver;
   ```
> IntelliJ will recognize these automatically if you added Selenium via Maven.

### 3. Create a WebDriver Instance
Create a new instance of the Chrome driver:
1. **Set WebDriver Path**:
```java
  WebDriver driver = new ChromeDriver(); // Selenium Manager handles the driver
   ```
- No need for System.setProperty if using Selenium 4.6+ with Maven.
- This line will launch a new Chrome browser window.

2. **Navigate to a Website**:
   - Use the WebDriver to navigate to a website.
   ```java
   driver.get("https://www.saucedemo.com/");
   ```

3. **Interact with Web Elements**:
   - Find and interact with web elements on the page.
   ```java
   WebElement searchBox = driver.findElement(By.name("q"));
   searchBox.sendKeys("Selenium");
   searchBox.submit();
   ```
   - `findElement(By.name("q"))` locates the search box.
   - `sendKeys()` types text into it.
   - `submit()` simulates pressing Enter.

4. **Verify Page Title**:
   - Verify that the page title contains the expected text.
   ```java
   String title = driver.getTitle();
   if (title.contains("Selenium")) {
       System.out.println("Test Passed");
   } else {
       System.out.println("Test Failed");
   }
   ```

5. **Close the Browser**:
   - Close the browser after the test is complete.
   ```java
   driver.quit();
   ```
   - Closes all browser windows and ends the session.

### 5. Complete Test Script

1. **Full Test Script**:
   - Combine all the steps into a complete test script.
   ```java
   import org.openqa.selenium.By;
   import org.openqa.selenium.WebDriver;
   import org.openqa.selenium.WebElement;
   import org.openqa.selenium.chrome.ChromeDriver;

   public class FirstSeleniumTest {
       public static void main(String[] args) {
         // Create a new ChromeDriver instance (Selenium Manager handles driver)
           WebDriver driver = new ChromeDriver();

        // Navigate to a website
        driver.get("https://www.saucedemo.com/");

        // Find the search box and perform a search
        WebElement searchBox = driver.findElement(By.name("q"));
        searchBox.sendKeys("Selenium");
        searchBox.submit();

        // Verify the page title
        String title = driver.getTitle();
        if (title.contains("Selenium")) {
            System.out.println("Test Passed");
        } else {
            System.out.println("Test Failed");
        }

        // Close the browser
        driver.quit();
       }
   }
   ```

### 6. Run the Test

1. **Execute the Test**:
   - Run the `FirstSeleniumTest` class to execute the test and verify that it works as expected.
      - In IntelliJ or Eclipse, right-click the class → Run `'FirstSeleniumTest'`.

Observe Chrome launching, performing the search, printing the test result, and closing.
> ✅ If it runs successfully, your Selenium setup and Maven project are correctly configured.

---

<div style="width: 100%">
<a href='introduction-to-selenium.md'><-- Previous Section: Introduction to Selenium</a>
<div align="right"><a href='first-selenium-script.md'> Next Section: First Selenium Script --></a></div>
</div>
