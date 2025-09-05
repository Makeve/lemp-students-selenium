# Setting Up Selenium

## Introduction

Setting up Selenium involves installing the necessary tools and configuring your environment to run Selenium tests. This guide will help you get started with Selenium WebDriver.

## Step-by-Step Guide

### 1. Install Java Development Kit (JDK)

1. **Download JDK**:
   - Go to the [Oracle JDK download page](https://www.oracle.com/java/technologies/javase-downloads.html).
   - Click on the `Download` button for the latest JDK version.
   - Choose your operating system (Windows, macOS, or Linux) and follow the prompts to download the installer.

2. **Install JDK**:
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

### 3. Install Selenium WebDriver

1. **Download WebDriver**: Download the WebDriver for your browser.
   - **ChromeDriver**: Go to the [ChromeDriver download page](https://sites.google.com/a/chromium.org/chromedriver/downloads) and download the latest version.
   - **GeckoDriver**: Go to the [GeckoDriver release page](https://github.com/mozilla/geckodriver/releases) and download the latest version.

2. **Install WebDriver**:
   - Extract the WebDriver executable from the downloaded archive.
   - Place the executable in a directory included in your system's `PATH`.

### 4. Create a Java Project and Add Selenium Jars

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

### 5. Verify Installation

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
