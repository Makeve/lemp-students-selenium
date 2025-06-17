[Back to Home](../README.md)

# Prerequisites: Configuring Laptops and Software Installation

## Introduction
This guide will help you set up your development environment by installing essential software and tools. Follow the steps below to configure your laptop and install the necessary software.

- [IntelliJ Installation](#ide)
- [Installing Git](#installinggit)
- [Installing Homebrew](#homebrew)
- [Installing Zsh](#zsh)
- [Verify Zsh Installation](#verifyzsh)
- [Install Java 17](#install-java-17)
- [Installing Maven](#maven)
- [Installing Chrome Driver](#chrome)
- [Installing Firefox (Gecko) Driver](#firefox)
- [Further Reading](#further)
- [Troubleshooting](#troubleshooting)

## Session Objective

This session will cover the following:

- IntelliJ Community Edition installation and extensions
- Git installation
- Homebrew installation
- Zsh installation
- Java installation
- Maven installation
- Chrome and Firefox Driver installation

## Detailed Steps

<a name="ide"></a>

## IntelliJ Installation

**IntelliJ Community Edition** is the IDE that we recommend using for Java Development.

### Steps to Install IntelliJ
1. **Download IntelliJ Community Edition**:
   - Go to IntelliJ for Mac [IntelliJ download page](https://www.jetbrains.com/idea/download/#section=mac)
   - Go to IntelliJ for Windows [IntelliJ download page](https://www.jetbrains.com/idea/download/#section=windows)
   - Choose the "Community" edition and download it for your operating system.

2. **Install IntelliJ**:
   - Follow the installation instructions for your operating system.
   - For Windows: Run the downloaded `.exe` file and follow the setup wizard.
   - For macOS: Open the downloaded `.dmg` file and drag IntelliJ to your Applications folder.
   - For Linux: Extract the downloaded `.tar.gz` file and run `./idea.sh` from the `bin` directory.

3. **Launch IntelliJ**:
   - Open IntelliJ IDEA from your applications or start menu.
   - Follow the setup wizard to configure IntelliJ according to your preferences.

<a name="installinggit"></a>

## Installing Git

### Steps to Install Git
1. **Download Git**:
   - Go to the [Git download page](https://git-scm.com/downloads).

2. **Install Git**:
   - For Windows: Run the downloaded `.exe` file and follow the setup wizard.
   - For macOS: Open the downloaded `.dmg` file and follow the setup instructions.
   - For Linux: Use your package manager (e.g., `sudo apt-get install git` for Ubuntu).

3. **Verify Git Installation**:
   - Open a terminal or command prompt.
   - Type `git --version` and press Enter.
   - You should see the installed Git version.

<a name="homebrew"></a>

## Install Homebrew

> Homebrew installs the stuff you need that Apple didn’t.

### Steps to Install Homebrew
1. **Open Terminal**:
   - Press `Command + Space` to open Spotlight Search, type "Terminal," and press Enter.

2. **Install Homebrew**:
   - Paste the following command into the terminal and press Enter:
     ```sh
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```

3. **Add Homebrew to PATH**:
   - Run these two commands in your terminal to add Homebrew to your PATH, replacing `johnsmith` with your profile name:
     ```sh
     (echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/johnsmith/.zprofile
     ```
     ```sh
     eval "$(/opt/homebrew/bin/brew shellenv)"
     ```

4. **Verify Homebrew Installation**:
   - Type `brew help` in the terminal and press Enter.
   - You should see a list of Homebrew commands and options.

<a name="zsh"></a>

## Install Zsh

### N.B. Windows users should skip this step

Zsh is a command shell that adds extra features to your regular terminal shell.

### Steps to Install Zsh
1. **Check Zsh Version**:
   - Open a terminal.
   - Type `zsh --version` and press Enter to see if Zsh is already installed.

2. **Install Zsh**:
   - If Zsh is not installed, type the following command and press Enter:
     ```sh
     brew install zsh zsh-completions
     ```

<a name="verifyzsh"></a>

## Verify Zsh Installation

### N.B. Windows users should skip this step

### Steps to Verify Zsh Installation
1. **Verify Zsh Version**:
   - Open a terminal.
   - Type `zsh --version` and press Enter.
   - Expected result: `zsh 5.1.1` or more recent.

2. **Make Zsh the Default Shell**:
   - Type the following command and press Enter:
     ```sh
     chsh -s /bin/zsh
     ```

3. **Log Out and Log In Again**:
   - Log out of your user account and log back in to use your new default shell.

4. **Test the Default Shell**:
   - Open a terminal.
   - Type `echo $SHELL` and press Enter.
   - Expected result: `/bin/zsh` or similar.

<a name="install-java-17"></a>

## Install Java 17

Oracle Java 8/9/10/11 is no longer supported with Selenium. You can install Java 17 from the official Oracle website.

### Steps to Install Java 17

#### For Mac Users:
1. **Go to the Oracle Java 17 download page**:
   - Navigate to [Java SE Development Kit 17 Downloads](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html).

2. **Download the macOS Installer**:
   - Scroll down to find the `macOS Installer` section.
   - Click on the link that says `jdk-17_macos-x64_bin.dmg` to download the installer.

3. **Install Java 17**:
   - Open the downloaded `.dmg` file.
   - Follow the on-screen instructions to complete the installation.

#### For Windows Users:
1. **Go to the Oracle Java 17 download page**:
   - Navigate to [Java SE Development Kit 17 Downloads](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html).

2. **Download the Windows Installer**:
   - Scroll down to find the `Windows Installer` section.
   - Click on the link that says `jdk-17_windows-x64_bin.exe` to download the installer.

3. **Install Java 17**:
   - Run the downloaded `.exe` file.
   - Follow the on-screen instructions to complete the installation.

<a name="maven"></a>

## Install Maven

### Steps to Install Maven
1. **Install Maven Using Homebrew**:
   - Open a terminal.
   - Type the following command and press Enter:
     ```sh
     brew install maven
     ```

2. **Install Maven Manually**:
   - If not using Homebrew, you can download Maven from the following links:
     - MacBook users: [Download Maven for Mac](https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz)
     - Windows users: [Download Maven for Windows](https://dlcdn.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.zip)
   - Extract the downloaded file and follow the installation instructions.

3. **Verify Maven Installation**:
   - Open a terminal or command prompt.
   - Type `mvn -version` and press Enter.
   - You should see the installed Maven version.

<a name="chrome"></a>

## Install Chrome Driver

We will be driving our Selenium tests using Chrome Driver.

### Steps to Install Chrome Driver
1. **Download Chrome Driver**:
   - For MacBook users: [Download Chrome Driver for Mac](https://edgedl.me.gvt1.com/edgedl/chrome/chrome-for-testing/126.0.6478.126/mac-arm64/chromedriver-mac-arm64.zip)
   - For Windows users: [Download Chrome Driver for Windows](https://edgedl.me.gvt1.com/edgedl/chrome/chrome-for-testing/126.0.6478.126/win64/chromedriver-win64.zip)

2. **Extract Chrome Driver**:
   - Extract the downloaded file to a location on your computer and make a note of where you save it.

3. **Add Chrome Driver to PATH**:
   - For macOS and Linux: Open a terminal and type the following command, replacing `/path/to/chromedriver` with the actual path to the extracted Chrome Driver:
     ```sh
     export PATH=$PATH:/path/to/chromedriver
     ```
   - For Windows: Open the System Properties, go to the "Advanced" tab, click on "Environment Variables," and add the path to the Chrome Driver to the `PATH` variable.

<a name="firefox"></a>

## Install Firefox (Gecko) Driver

We will also be driving our Selenium tests using Gecko Driver.

### Steps to Install Gecko Driver
1. **Download Gecko Driver**:
   - For MacBook users: [Download Gecko Driver for Mac](https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-macos-aarch64.tar.gz)
   - For Windows users: [Download Gecko Driver for Windows](https://github.com/mozilla/geckodriver/releases/download/v0.34.0/geckodriver-v0.34.0-win-aarch64.zip)

2. **Extract Gecko Driver**:
   - Extract the downloaded file to a location on your computer and make a note of where you save it.

3. **Add Gecko Driver to PATH**:
   - For macOS and Linux: Open a terminal and type the following command, replacing `/path/to/geckodriver` with the actual path to the extracted Gecko Driver:
     ```sh
     export PATH=$PATH:/path/to/geckodriver
     ```
   - For Windows: Open the System Properties, go to the "Advanced" tab, click on "Environment Variables," and add the path to the Gecko Driver to the `PATH` variable.

<a name="further"></a>

## Further Reading

- [The IntelliJ Website](https://www.jetbrains.com/idea/download/#section=mac)
- [What is Git?](https://www.atlassian.com/git/tutorials/what-is-git)
- [What is Zsh?](https://ohmyz.sh/)
- [What is Homebrew?](https://brew.sh/)
- [Apache Maven](https://maven.apache.org/)

- [Top](#Session-Objective)

- [Back to Main](index.md)

<a name="troubleshooting"></a>

## Troubleshooting

### Common Issues and Solutions

- **IntelliJ Installation Problems**:
  - If you encounter issues during installation, refer to the [IntelliJ Installation Troubleshooting Guide](https://www.jetbrains.com/idea/help/installation-guide.html).

- **Git Installation Problems**:
  - If Git is not recognized as a command, ensure it is installed correctly and its path is added to the system's PATH environment variable.

- **Homebrew Installation Problems**:
  - If Homebrew installation fails, make sure you have the necessary permissions and try running the installation command with `sudo`.

- **Zsh Installation Problems**:
  - If Zsh is not recognized, ensure it is installed correctly and its path is added to the system's PATH environment variable.

- **Java Installation Problems**:
  - If Java is not recognized, ensure it is installed correctly and its path is added to the system's PATH environment variable.

- **Maven Installation Problems**:
  - If Maven is not recognized, ensure it is installed correctly and its path is added to the system's PATH environment variable.

- **Driver Installation Problems**:
  - If the drivers are not recognized, ensure their paths are added to the system's PATH environment variable correctly.

If you encounter further issues, feel free to reach out for assistance.

---

<div style="width: 100%">
<a href='index.md'><-- Previous Section: Introduction</a>
<div align="right"><a href='intro_to_git.md'>Next Section: Introduction to Git --></a></div>
</div>

