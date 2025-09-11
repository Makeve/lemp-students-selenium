# 🏋️ Selenium Exercise: Writing Scripts to Interact with Web Elements  

Now that you’ve learned about different locators, let’s practice by writing **real Selenium scripts** to interact with web elements.  

## 📝 Exercise 1: Writing Selenium Script to Perform a Google Search  

**Test Case: Search in Google**  

In this exercise, you will write a Selenium script to perform a search on Google.  

### Steps  
1. Open a web browser and navigate to [Google](https://www.google.com).  
2. Locate the search input field using its **name** attribute.  
3. Enter the search term **"Selenium WebDriver"** into the search input field.  
4. Submit the search form.  
5. Verify that the search results page is displayed.  

## ✅ Sample Solution (Java + Selenium)  

<details>
<summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class GoogleSearchTest {
    public static void main(String[] args) {
        // 1. Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Navigate to Google
        driver.get("https://www.google.com");

        // 3. Locate the search input field by its name attribute
        WebElement searchField = driver.findElement(By.name("q"));

        // 4. Enter the search term
        searchField.sendKeys("Selenium WebDriver");

        // 5. Submit the search form
        searchField.submit();

        // 6. Verify that the search results page is displayed
        String title = driver.getTitle();
        if (title.contains("Selenium WebDriver")) {
            System.out.println("Test Passed ✅");
        } else {
            System.out.println("Test Failed ❌");
        }

        // 7. Close the browser
        driver.quit();
    }
}
```
</details>

## Exercise 2: Interacting with Buttons, Checkboxes & Radio Buttons

### Test Case: Login Form Automation

In this exercise, you will write a Selenium script to automate a login form.

#### Steps:
1. Open a web browser and navigate to the login page.
2. Locate the username input field using its ID attribute.
3. Locate the password input field using its ID attribute.
4. Locate the login button using its name attribute.
5. Enter the username and password.
6. Click the login button.
7. Verify that the login was successful by checking the presence of a specific element.

## ✅ Sample Solution (Java + Selenium)
<details> <summary>💡 Click here to view the solution</summary>

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginFormTest {
    public static void main(String[] args) {
        // 1. Create a new instance of the ChromeDriver
        WebDriver driver = new ChromeDriver();

        // 2. Navigate to the login page
        driver.get("https://example.com/login");

        // 3. Locate the username input field by its ID attribute
        WebElement usernameField = driver.findElement(By.id("username"));

        // 4. Locate the password input field by its ID attribute
        WebElement passwordField = driver.findElement(By.id("password"));

        // 5. Locate the login button by its name attribute
        WebElement loginButton = driver.findElement(By.name("login"));

        // 6. Enter the username
        usernameField.sendKeys("your-username");

        // 7. Enter the password
        passwordField.sendKeys("your-password");

        // 8. Click the login button
        loginButton.click();

        // 9. Verify that the login was successful by checking the presence of a specific element
        WebElement dashboardElement = driver.findElement(By.id("dashboard"));
        if (dashboardElement.isDisplayed()) {
            System.out.println("Login Test Passed ✅");
        } else {
            System.out.println("Login Test Failed ❌");
        }

        // 10. Close the browser
        driver.quit();
    }
}
```
</details>

### 🎯 Practice 

Practice these exercises to become proficient in writing Selenium scripts to interact with various web elements.  

Try modifying the scripts to:  
- Use different locators (`id`, `name`, `cssSelector`, `xpath`).  
- Test with other websites or forms.  
- Add validation for multiple elements.  


<div style="width: 100%">
<a href='7_xpath_locator.md'><-- Previous Section: Xpath Locator</a>
<div align="right"><a href='hands-on-exercise.md'> Next Section: Hands-on Exercise --></a></div>
</div>
