# Setting Up Selenium

## Introduction

Setting up Selenium involves installing the necessary tools and configuring your environment to run Selenium tests. This guide will help you get started with Selenium WebDriver.

## Step-by-Step Guide

### 1. Install Java Development Kit (JDK)

1. **Download JDK**:
   - Go to the [Oracle JDK download page](https://www.oracle.com/java/technologies/javase-downloads.html).
   - Click on the `Download` button for the latest JDK version.
   - Choose your operating system (Windows, macOS, or Linux) and follow the prompts to download the installer.

1. **Install JDK**:
   - **Windows**: Run the downloaded `.exe` file and follow the setup wizard.
   - **macOS**: Open the downloaded `.dmg` file and follow the installation instructions.
   - **Linux**: Follow the instructions on the download page to install the JDK.

### 2. Set Up Environment Variables

1. **Configure JAVA_HOME**:
   - **Windows**:
     1. Right-click on `This PC` or `Computer` and select `Properties`.
     2. Click on `Advanced system settings`.
     3. Click on `Environment Variables`.
     4. Click `New` under `System variables`.
     5. Enter `JAVA_HOME` as the variable name and the path to your JDK installation as the variable value.
     6. Add the JDK `bin` directory to the `Path` variable by selecting `Path`, clicking `Edit`, and adding the path to the JDK `bin` directory.
   - **macOS and Linux**:
     1. Open your terminal.
     2. Open your shell configuration file (e.g., `.bashrc`, `.zshrc`) by running:
        ```sh
        nano ~/.bashrc
        ```
     3. Add the following lines to the file:
        ```sh
        export JAVA_HOME=/path/to/jdk
        export PATH=$JAVA_HOME/bin:$PATH
        ```
     4. Save and apply the changes by running:
        ```sh
        source ~/.bashrc
        ```

### 3. Install Selenium WebDriver (Reference / Optional)

> **Note:** If you are using Maven with Selenium 4.6 or newer, you **do not need to manually download WebDriver**. Selenium Manager handles it automatically.  
> The following steps are for **reference or restricted network environments**.

1. **Download WebDriver**: Download the WebDriver for your browser.
   - **ChromeDriver**: Go to the [ChromeDriver download page](https://sites.google.com/a/chromium.org/chromedriver/downloads) and download the latest version.
   - **GeckoDriver**: Go to the [GeckoDriver release page](https://github.com/mozilla/geckodriver/releases) and download the latest version.

2. **Install WebDriver**:
   - Extract the WebDriver executable from the downloaded archive.
   - Place the executable in a directory included in your system's `PATH`.
  
### 4. ⚠️ Important: Verify ChromeDriver Matches Your Chrome Browser (Reference / Optional)

ChromeDriver must **match the major version** of the installed Chrome browser (e.g., Chrome **128.x** ↔︎ ChromeDriver **128.x**).  
If you downloaded ChromeDriver weeks ago (for example, in Lecture 1), check now to make sure it still matches your current Chrome version.

#### 4a. Check Your Chrome Version

- **Windows (GUI method)**
  1. Open Chrome.
  2. Click the **⋮** menu → **Help** → **About Google Chrome**.
  3. Note the version number (e.g., `128.0.6613.84`). The **first number** (`128`) is the major version.

- **Windows (PowerShell method)**
  ```powershell
  (Get-Item "C:\Program Files\Google\Chrome\Application\chrome.exe").VersionInfo.ProductVersion

- **macOS (GUI method)**
 1. Open Chrome.
 2. Click Chrome (menu bar) → About Google Chrome.
 3. Note the version number (major = first number).

- **macOS (Terminal method)**
  ``` bash
  /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --version

#### 4b. Check Your ChromeDriver Version
- **Windows**
   - If `chromedriver` is on your `PATH`:
  ```powersheel
  chromedriver --version
  ```
   - If it’s in a folder (e.g., Downloads):
  ```powershell
  .\chromedriver.exe --version
   ```
   - Or right-click → Properties → Details → File version.
 
- **macOS**
  - If `chromedriver` is on your `PATH`:
  ```bash
  chromedriver --version
  ```
  - If it’s in a folder (e.g., Downloads):
    ```bash
    cd /path/to/folder
    ./chromedriver --version
> **Note (macOS users):**  
> If you see a **permission warning**, make the file executable:  
> ```bash
> chmod +x chromedriver
> ```  
>  
> If macOS blocks it with **“cannot be opened”**, go to:  
> **System Settings → Privacy & Security** and click **Allow Anyway**,  
> then run the command again.

#### 4c. Compare the Versions
   - Example:
      - Chrome: `128.0.6613.84` → major 128
      - ChromeDriver: `128.0.6613.86` → major 128 → ✅ Works
   - If the first number doesn’t match → ❌ mismatch.

#### 4d. Fixing a Mismatch

- Option 1: Update ChromeDriver
   1. Note your Chrome major version.
   2. Download the matching ChromeDriver from the official site.
   3. Replace the old `chromedriver` with the new one.

- Option 2: Update Chrome
   1. Go to About Google Chrome and update.
   2. Then download the matching ChromeDriver.

- Option 3: or use Selenium Manager (recommended)

#### 4e. Common Pitfalls (Reference / Optional)
- Multiple `chromedriver` executables on your system
   - Windows: `where chromedriver`
   - macOS: `which -a chromedriver`
      → Remove or rename old versions.
- On macOS, you may need to remove the “quarantine” flag:
  ```bash
  xattr -d com.apple.quarantine /path/to/chromedriver
- On Apple Silicon (M1/M2 Macs), ensure you download the correct ARM64 ChromeDriver build.

### 5: Use Selenium Manager (Selenium ≥ 4.6) (Recommended)
   - Selenium Manager automatically downloads the right driver.
   - You don’t need to set `webdriver.chrome.driver` manually.
 ```java
  // Example with Selenium 4.6+
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class SeleniumTest {
    public static void main(String[] args) {
        // No need to set driver path
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.example.com");
        System.out.println("Title: " + driver.getTitle());
        driver.quit();
    }
}
```
   - No System.setProperty needed.
   - Maven + Selenium 4.6+ automatically downloads the correct driver.
  
### 6. Add Selenium to Your Maven Project (Recommended)

Since we are using a **Maven project** (archetype quickstart), we don’t need to manually download Selenium JARs or browser drivers.  
Maven will handle downloading Selenium libraries, and **Selenium Manager** (included in Selenium 4.6+) will automatically download the correct ChromeDriver when you run your tests.

   #### 6a. Update Java Version in Maven

Selenium 4 requires **Java 11 or higher**.  
Update your `pom.xml` properties section:

```xml
<properties>
  <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  <maven.compiler.source>17</maven.compiler.source>
  <maven.compiler.target>17</maven.compiler.target>
</properties>
```
   #### 6b. Add Selenium Dependency
Add the following inside the `<dependencies>` section of your `pom.xml`:
```xml
<dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>

    <!-- Selenium with Selenium Manager included -->
    <dependency>
      <groupId>org.seleniumhq.selenium</groupId>
      <artifactId>selenium-java</artifactId>
      <version>4.12.1</version> <!-- or latest stable -->
    </dependency>
</dependencies>
```
> **Note:** You can check the version of Selenium you are using by opening External Libraries in IntelliJ after Maven downloads the dependencies.

   #### 6c. Create a Simple Test Using Selenium Manager

Create a new Java class, e.g., `SeleniumTest.java`, in `src/main/java`.
Example test:
```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class SeleniumTest {
    public static void main(String[] args) {
        // Selenium Manager automatically resolves the correct driver
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.example.com");
        System.out.println("Title: " + driver.getTitle());
        driver.quit();
    }
}
```
   - ✅ No `System.setProperty("webdriver.chrome.driver", ...)` needed.
   - On the first run, Selenium Manager downloads the matching ChromeDriver automatically.

   #### 6d. Run Your Test

1. In IntelliJ, right-click `SeleniumTest.java` → Run `'SeleniumTest.main()'`.
2. Check that Chrome opens, navigates to the site, prints the title, and closes.

> If everything works, your Maven project is fully configured with Selenium and Selenium Manager, and you no longer need to download ChromeDriver manually.

## Optional: Using Selenium JARs Manually

> **Note for Maven users:** If you are using a Maven project (like our archetype-quickstart) with Selenium 4.6 or newer, you **do not need to download the Selenium JARs manually**.  
> Maven will automatically download the correct Selenium libraries when you add the dependency in `pom.xml`, and Selenium Manager will handle the browser driver for you.  

The manual JAR approach is only necessary if:

- You are **not using Maven** (or Gradle), or  
- You are working in a **restricted environment** where Maven cannot download dependencies from the internet.

For most students, the **Maven dependency approach is simpler and recommended**, but the steps below are kept for reference if needed.

### Create a Java Project and Add Selenium Jars - 

#### 1. Create an Empty Java Project in Your IDE (IntelliJ or Eclipse)

1. **IntelliJ**:
   - Open IntelliJ IDEA.
   - Go to `File` > `New` > `Project`.
   - Select `Java`, then click `Next`.
   - Enter the project name and location, then click `Finish`.

2. **Eclipse**:
   - Open Eclipse.
   - Go to `File` > `New` > `Java Project`.
   - Enter the project name and click `Finish`.

#### 2. Download the Selenium Jars

1. **Download Selenium Jars**:
   - Go to the [official Selenium website](https://www.selenium.dev/downloads/).
   - Scroll down to the section 'Selenium Clients and WebDriver Language Bindings'.
   ![selenium_bindings](../resources/selenium_webdriver_architecture/selenium_bindings.PNG)
   - Click on the latest stable version link to download the files.
   - Save and unzip the selenium-java folder.

#### 3. Add Jar Dependencies to the Project

1. **IntelliJ**:
   - Right-click on the project name and select `Open Module Settings`.
   - Under `Project Settings`, select `Modules` and then select the `Dependencies` tab.
   - Click on the `+` icon > `Library` > `Java`.
   - Select the unzipped selenium-java folder and then click `OK`.
   ![add_selenium_lib](../resources/selenium_webdriver_architecture/IntelliJ_project_settings.PNG)
   ![add_selenium_lib](../resources/selenium_webdriver_architecture/IntelliJ_project_modules.PNG)
   - Ensure that the SDK is pointing to the Java 17 library that you installed earlier.
     - Go to `Project` in the left pane.
     - Ensure the `Project SDK` is set to Java 17. If not, click `New` and select the path where you installed Java 17.
   - You will also need to add the `lib` folder within the selenium-java folder directory as an additional dependency.
     - Click on the `+` icon > `Library` > `Java`.
     - Select the `lib` folder within the unzipped selenium-java directory and click `OK`.
![image](https://github.com/user-attachments/assets/a6f2aa35-a27a-4d14-9d6d-cac99ebff35f)

![image](https://github.com/user-attachments/assets/e91ea203-7c10-4afd-b6a0-030f603c3eef)


2. **Eclipse**:
   - Right-click on the project name and select `Properties`.
   - Go to `Java Build Path` and select the `Libraries` tab.
   - Click on `Add External JARs`.
   - Select the unzipped selenium-java folder and add all the `.jar` files.
   - Also add the `.jar` files from the `lib` folder within the selenium-java directory.

#### 4. Verify Installation

1. **Write a Simple Test**: Create a new Java class and write a simple test to verify the setup.
   ```java
   import org.openqa.selenium.WebDriver;
   import org.openqa.selenium.chrome.ChromeDriver;

   public class SeleniumTest {
       public static void main(String[] args) {
           // Set the path to the WebDriver executable
           System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");

           // Create a new instance of the Chrome driver
           WebDriver driver = new ChromeDriver();

           // Navigate to a website
           driver.get("https://www.example.com");

           // Print the title of the page
           System.out.println("Title: " + driver.getTitle());

           // Close the browser
           driver.quit();
       }
   }
   ```

2. **Run the Test**: Run the test to ensure everything is set up correctly.

---

<div style="width: 100%">
<a href='introduction-to-selenium.md'><-- Previous Section: Introduction to Selenium</a>
<div align="right"><a href='writing-your-first-test.md'> Next Section: Writing Your First Test --></a></div>
</div>
