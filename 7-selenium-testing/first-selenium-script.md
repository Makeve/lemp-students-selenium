# First Selenium Script - Writing Your First Test

### Introduction

In this section, we’ll write our first Selenium test in Java 🎉.

A Selenium test is simply a Java program that:

1. Opens a browser (e.g., Chrome).
2. Navigates to a website.
3. Finds elements on the page.
4. Interacts with those elements (typing, clicking, etc.).
5. Checks (verifies) that the expected result happens.

By the end, you’ll have a working test script that you can run in IntelliJ.

## Selenium WebDriver

### 1. Create a New Test Class

When you created the Maven project with `archetype-quickstart`, it gave you a default class called `App.java`.

Instead of editing that file, it’s better to create a new Java class for each test you want to write.

1. In IntelliJ, right-click the `src/main/java/com.saucedemo` package.
2. Select New → Java Class.
3. Name the class:
   ```java
   FirstSeleniumTest
   ```
This will give you an empty Java file where we’ll write our test.

### 2: Import Selenium Libraries

Since we added Selenium dependencies in pom.xml, Maven downloaded them automatically for us.

Now, we just need to import the classes we’ll use in our test:
```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
```

### 3. Opening and Closing a Webpage

Selenium WebDriver lets you open and close browser windows.
```java
WebDriver driver = new ChromeDriver();
driver.get("https://www.saucedemo.com/");
driver.quit();
```
- `get()` → opens the given URL in Chrome.
- At this point, you should see the Sauce Demo login page open in your browser.
- `quit()` → closes the browser and ends the WebDriver session.


### 4. Configuring Browser Options

By default, when you run Selenium tests, Chrome opens in a normal visible browser window. But sometimes you’ll want to customize how Chrome runs, such as:
- Running in headless mode (no visible browser window, useful for servers or CI/CD).
- Setting the window size.
- Disabling unnecessary extensions or notifications.

Selenium lets us do this with the `ChromeOptions` class.

You can pass options to Chrome, for example running in headless mode:
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class FirstSeleniumTest {
    public static void main(String[] args) {
        // Create ChromeOptions object to configure browser behavior
        ChromeOptions options = new ChromeOptions();

        // Run without opening a browser window
        options.addArguments("--headless");  

        // Set a fixed window size (important for headless mode)
        options.addArguments("window-size=1200x600");

        // Pass options into ChromeDriver
        WebDriver driver = new ChromeDriver(options);

        // Open the website
        driver.get("https://www.saucedemo.com/");

        // Print page title
        System.out.println("Title: " + driver.getTitle());

        // Close browser
        driver.quit();
    }
}
```
- `ChromeOptions options = new ChromeOptions();`

   Creates an object to hold special settings for Chrome.

- `options.addArguments("--headless");`

   Tells Chrome to run in headless mode (no window is displayed). This is useful for automation environments like Jenkins, Docker, or cloud servers    that don’t have a desktop.

- `options.addArguments("window-size=1200x600");`

   Sets the screen size for the headless browser. Without this, some websites may load in mobile layout, which could break tests.

- `new ChromeDriver(options);`

   Instead of starting Chrome with default settings, we give it the customized `options`.

#### Other Common Options

You can configure Chrome with many other arguments. Some useful ones:

- `--incognito` → Launch in incognito mode.
- `--disable-extensions` → Disable Chrome extensions.
- `--start-maximized` → Start with the browser maximized.
- `--disable-notifications` → Prevent popups/notifications.

Example:
```java
options.addArguments("--incognito");
options.addArguments("--start-maximized");
```
#### Best Practice:
Even if you don’t always use headless mode, it’s important to understand how to configure ChromeOptions. Most real-world projects will use it to stabilize tests and make them work in different environments.

### 5. Locating Elements

Selenium provides multiple strategies for finding elements:
```java
WebElement byId = driver.findElement(By.id("user-name"));
WebElement byName = driver.findElement(By.name("password"));
WebElement byCss = driver.findElement(By.cssSelector(".btn_action"));
WebElement byXpath = driver.findElement(By.xpath("//input[@id='user-name']"));
```
### 6. Interacting with Elements

Examples of interactions:
```java
// Enter text
driver.findElement(By.id("user-name")).sendKeys("standard_user");

// Click a button
driver.findElement(By.className("btn_action")).click();
```
### 7. Using Waits (Synchronization)

Sometimes elements take time to load. Selenium provides two main types of waits:
1. Implicit Wait: Tells WebDriver to wait for a certain amount of time when searching for elements.
   ```java
   driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
   ```
   - This means Selenium will try for up to 10 seconds to find an element before throwing an error.
2. Explicit Wait: Waits for a specific condition to be true (e.g., element visible, clickable).
   ```java
   import org.openqa.selenium.support.ui.WebDriverWait;
   import org.openqa.selenium.support.ui.ExpectedConditions;
   import java.time.Duration;
   
   // Wait up to 20 seconds for the element to be visible
   WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(20));
   WebElement username = wait.until(
           ExpectedConditions.visibilityOfElementLocated(By.id("user-name"))
   );
   username.sendKeys("standard_user");
   ```
3. Best Practice:
- Use explicit waits for elements that are dynamic.
- Keep implicit waits short (or off) to avoid hidden timing issues.

### 8. Taking Screenshots
```java
File screenshot = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
Files.copy(screenshot.toPath(), Path.of("screenshot.png"));
```
### 9. Validating with Assertions

You can use JUnit (already included in your Maven Quickstart project) for assertions:
```java
import org.junit.Assert;

Assert.assertEquals("Swag Labs", driver.getTitle());
Assert.assertTrue(driver.findElement(By.id("user-name")).isDisplayed());
```

## Appendix: Manual Setup (Reference Only)

⚠️ This section is only for **historical reference** or for environments where you cannot use Maven and Selenium Manager (for example, restricted projects or offline machines).  

In our course setup, you **do not need to do this**. Just skip to the next section if you’re using Maven. In older projects, every browser driver (ChromeDriver, GeckoDriver, etc.) had to be downloaded manually and referenced with System.setProperty.

Now, Selenium Manager automates this, which is why we didn’t need it in our main flow.

Example:
```java
public class Basics {
    public static void main(String[] args) {
        // Manually tell Selenium where ChromeDriver is
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");

        WebDriver driver = new ChromeDriver();
        driver.get("https://www.saucedemo.com/");
        driver.quit();
    }
}
```

### 1. Create a New Java Class → Skip, Maven archetype already set it up. 
1. **Open your IDE (Integrated Development Environment)**: This could be IntelliJ IDEA, Eclipse, or any other Java IDE you prefer.
2. **Create a New Project**:
   - Go to `File > New > Project`.
   - Select `Java` and click `Next`.
   - Name your project (e.g., `SeleniumFirstScript`) and choose the project location.
   - Click `Finish`.

3. **Create a New Java Class**: → Optional.
   - In the Project Explorer, right-click the `src` folder.
   - Select `New > Java Class`.
   - Name your class (e.g., `Basics`) and click `Finish`.

4. **Add a Main Method to the Java Class**:
   - In the newly created `Basics` class, add the `main` method.
   - Shortcut: Type `psvm` and hit `Enter`.

```java
public class Basics {
    public static void main(String[] args) {
        // Your code will go here
    }
}
```

### 2. Set System Property to ChromeDriver
1. **Download ChromeDriver**:
   - Go to the ChromeDriver download page: [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads)
   - Download the version that matches your installed Chrome browser version.
   - Extract the downloaded file to a location on your system (e.g., `C:\drivers\chromedriver.exe`).

2. **Set System Property in Your Code**:
   - Set the `webdriver.chrome.driver` property to the path of your ChromeDriver executable.

```java
public class Basics {
    public static void main(String[] args) {
        // Set the path to the ChromeDriver executable
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        
        // Create an instance of ChromeDriver
        WebDriver driver = new ChromeDriver();
    }
}
```

<i>Information: WebDriver is a Java interface that has a set of unimplemented methods that are common across browsers. Individual browsers then have their own Java class that implements the methods of WebDriver, for example, ChromeDriver, FirefoxDriver, EdgeDriver. This allows your Selenium automation scripts to be generic and have the ability to execute across different browsers with the same methods. For more information, see the [WebDriver documentation](https://www.selenium.dev/selenium/docs/api/java/org/openqa/selenium/WebDriver.html).</i>

### 3. Tell Selenium ChromeDriver to Open a Webpage
1. **Use the `get` Method to Open a Webpage**:
   - The `get` method loads a new web page in the current browser window.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        // Open the specified URL
        driver.get("https://www.saucedemo.com/");
    }
}
```

**Explanation**: Once you execute the script, the Chrome browser should be invoked and open up the specified URL, in this case, https://www.saucedemo.com.

### 4. Tell Selenium ChromeDriver to Open a Webpage and Then Close It
1. **Use the `quit` Method to Close the Browser**:
   - The `quit` method closes all browser windows and ends the WebDriver session.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        // Open the specified URL
        driver.get("https://www.saucedemo.com/");
        
        // Close the browser
        driver.quit();
    }
}
```

**Explanation**: Once you execute the script, the Chrome browser should be invoked, open up the specified URL, in this case, https://www.saucedemo.com, and then close it.

### 5. Managing WebDriver Instances
**Best Practices for Managing WebDriver Instances**:
   - Always quit the driver instance at the end of the test to free up resources.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Close the current window
        driver.close();
        
        // Quit the WebDriver session
        driver.quit();
    }
}
```

### 6. Handling Browser Windows and Frames
**Switch Between Multiple Browser Windows or Tabs and Frames**:

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Switching to a new window
        for (String windowHandle : driver.getWindowHandles()) {
            driver.switchTo().window(windowHandle);
        }
        
        // Switching to a frame
        driver.switchTo().frame("frameName");
        
        // Close the browser
        driver.quit();
    }
}
```

### 7. Assertions and Validations
**Use Assertions to Validate Test Results**:

```java
import org.junit.Assert;

public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Validating title
        Assert.assertEquals(driver.getTitle(), "Swag Labs");
        
        // Validating element visibility
        Assert.assertTrue(driver.findElement(By.id("user-name")).isDisplayed());
        
        // Close the browser
        driver.quit();
    }
}
```
---

<div style="width: 100%">
<a href='writing-your-first-test.md'><-- Previous Section: Writing Your First Test</a>
<div align="right"><a href='different-browsers.md'> Next Section: Webdriver Different Browsers --></a></div>
</div>
