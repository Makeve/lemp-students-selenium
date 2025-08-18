# IDE Configuration

## Introduction

Configuring your Integrated Development Environment (IDE) is essential for improving productivity and ensuring a smooth development workflow. This guide will focus on configuring IntelliJ IDEA, one of the most popular IDEs for Java development.

## Step-by-Step Guide

### 1. Install IntelliJ IDEA

1. **Download IntelliJ IDEA**:
   - Go to the [IntelliJ download page](https://www.jetbrains.com/idea/download/#section=mac).
   - Click on the `Download` button under the Community Edition.
   - Choose your operating system (Windows, macOS, or Linux) and follow the prompts to download the installer.

2. **Install IntelliJ IDEA**:
   - **Windows**: Run the downloaded `.exe` file and follow the setup wizard.
   - **macOS**: Open the downloaded `.dmg` file and drag IntelliJ IDEA to your Applications folder.
   - **Linux**: Extract the downloaded `.tar.gz` file and run `./idea.sh` from the `bin` directory.

### 2. Configure IntelliJ IDEA

#### Set Up a New Project

1. **Open IntelliJ IDEA**: Launch IntelliJ IDEA from your applications or start menu.
2. **Create a New Project**:
   - Click on `File` > `New` > `Project`.
   - Select the project type (e.g., Java, Maven).
   - Click `Next`.
   - Enter the project details (e.g., Project name, Location) and click `Finish`.

#### Customize Appearance and Behavior

1. **Appearance**:
   - Go to `File` > `Settings` (or `IntelliJ IDEA` > `Preferences` on macOS) > `Appearance & Behavior` > `Appearance`.
   - Choose your preferred theme (e.g., Dark, Light).

2. **Keymap**:
   - Go to `File` > `Settings` > `Keymap`.
   - Choose a predefined keymap (e.g., Default, Eclipse) or customize your own.

3. **Editor**:
   - Go to `File` > `Settings` > `Editor`.
   - Configure options like font size, code style, and color scheme.

### 3. Install Essential Plugins

1. **Open the Plugin Marketplace**:
   - Go to `File` > `Settings` > `Plugins`.
   - Click on `Marketplace`.

2. **Install Plugins**:
   - Search for and install essential plugins like `Lombok`, `CheckStyle-IDEA`, `SonarLint`, etc.
   - Click `Install` next to the desired plugin and restart IntelliJ IDEA if prompted.

### 4. Set Up Version Control

1. **Configure Git**:
   - Go to `File` > `Settings` > `Version Control` > `Git`.
   - Ensure the path to the Git executable is correct. If it's not auto-detected, you can set it manually.

2. **Clone a Repository**:
   - Go to `File` > `New` > `Project from Version Control`.
   - Enter the repository URL and click `Clone`.

### 5. Configure Build Tools

#### Set Up Maven

1. **Open Maven Settings**:
   - Go to `File` > `Settings` > `Build, Execution, Deployment` > `Build Tools` > `Maven`.

2. **Set Maven Home Directory**:
   - If the Maven home directory is not auto-detected:
     1. Download Maven from the [Maven download page](https://maven.apache.org/download.cgi).
     2. Extract the downloaded archive to a directory of your choice.
     3. In IntelliJ IDEA, click on the `...` button next to the `Maven home directory` field.
     4. Navigate to the directory where you extracted Maven and select it.
     5. Click `OK` to save the changes.

#### Set Up Gradle

1. **Open Gradle Settings**:
   - Go to `File` > `Settings` > `Build, Execution, Deployment` > `Build Tools` > `Gradle`.

2. **Set Gradle Home Directory**:
   - Ensure the Gradle home directory is set correctly. If it's not auto-detected, follow the detailed setup instructions [here](build-tools.md#set-up-gradle).

---

<div style="width: 100%">
<a href='introduction.md'><-- Previous Section: Introduction to Development Environment</a>
<div align="right"><a href='useful-plugins.md'>Next Section: Useful Plugins--></a></div>
</div>
