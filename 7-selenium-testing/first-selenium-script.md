# First Selenium Script
## Selenium WebDriver

### 1. Create a New Java Class
1. **Open your IDE (Integrated Development Environment)**: This could be IntelliJ IDEA, Eclipse, or any other Java IDE you prefer.
2. **Create a New Project**:
   - Go to `File > New > Project`.
   - Select `Java` and click `Next`.
   - Name your project (e.g., `SeleniumFirstScript`) and choose the project location.
   - Click `Finish`.

3. **Create a New Java Class**:
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

### 5. Handling Browser Options and Capabilities
1. **Configure ChromeDriver with Specific Options**:
   - You can set various options such as running in headless mode, disabling extensions, and setting the window size.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        
        // Configure ChromeOptions
        ChromeOptions options = new ChromeOptions();
        options.addArguments("--headless");
        options.addArguments("--disable-extensions");
        options.addArguments("window-size=1200x600");
        
        // Create an instance of ChromeDriver with options
        WebDriver driver = new ChromeDriver(options);
        
        // Open the specified URL
        driver.get("https://www.saucedemo.com/");
        
        // Close the browser
        driver.quit();
    }
}
```

### 6. Managing WebDriver Instances
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

### 7. Implicit and Explicit Waits
**Implementing Implicit and Explicit Waits**:
   - Waits help synchronize your script with the state of web elements.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        // Implicit Wait
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
        
        // Open the specified URL
        driver.get("https://www.saucedemo.com/");
        
        // Explicit Wait
        WebDriverWait wait = new WebDriverWait(driver, 20);
        WebElement element = wait.until(ExpectedConditions.visibilityOfElementLocated(By.id("user-name")));
        
        // Close the browser
        driver.quit();
    }
}
```

### 8. Locating Elements
**Different Strategies for Locating Elements**:
   - Use various strategies such as ID, name, class name, CSS selector, and XPath.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Locating elements
        WebElement byId = driver.findElement(By.id("user-name"));
        WebElement byName = driver.findElement(By.name("password"));
        WebElement byClassName = driver.findElement(By.className("btn_action"));
        WebElement byCssSelector = driver.findElement(By.cssSelector(".btn_action"));
        WebElement byXPath = driver.findElement(By.xpath("//input[@id='user-name']"));
        
        // Close the browser
        driver.quit();
    }
}
```

### 9. Interacting with Web Elements
**Common Interactions with Web Elements**:
   - Clicking buttons, entering text, selecting from dropdowns, and handling alerts.

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Clicking a button
        WebElement button = driver.findElement(By.className("btn_action"));
        button.click();
        
        // Entering text
        WebElement inputField = driver.findElement(By.id("user-name"));
        inputField.sendKeys("standard_user");
        
        // Selecting from a dropdown (if applicable)
        Select dropdown = new Select(driver.findElement(By.id("dropdownId")));
        dropdown.selectByVisibleText("Option");
        
        // Handling alerts (if applicable)
        Alert alert = driver.switchTo().alert();
        alert.accept();
        
        // Close the browser
        driver.quit();
    }
}
```

### 10. Taking Screenshots
**Capture Screenshots During Test Execution**:

```java
public class Basics {
    public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver", "C:\\drivers\\chromedriver.exe");
        WebDriver driver = new ChromeDriver();
        
        driver.get("https://www.saucedemo.com/");
        
        // Capture screenshot
        File screenshot = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
        try {
            FileUtils.copyFile(screenshot, new File("path/to/screenshot.png"));
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        // Close the browser
        driver.quit();
    }
}
```

### 11. Handling Browser Windows and Frames
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

### 12. Assertions and Validations
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
<div align="right"><a href='webdriver-basic-methods.md'> Next Section: Webdriver Basic Methods --></a></div>
</div>
