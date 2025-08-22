# Build Tools

## Introduction

Build tools automate the process of compiling code, packaging binaries, running tests, and deploying applications. This guide will introduce you to some of the most commonly used build tools in Java development.

## Maven

### What is Maven?

Maven is a build automation tool primarily used for Java projects. It simplifies the build process by managing project dependencies, compiling code, running tests, and packaging the application.

### Step-by-Step Guide

1. **Install Maven**:
   - Follow the instructions in the [Configuration Guide](../course-requirements/course-reqs_section_01.md) to install Maven.

2. **Create a Maven Project**:
   - Open IntelliJ IDEA.
   - Go to `File` > `New` > `Project`.
   - Select `Maven` and click `Next`.
   - Enter the project details (e.g., GroupId, ArtifactId) and click `Finish`.
  
- Click **Next**.

## **3. Configure Maven Coordinates**
Fill in the fields:

| Field        | Example Value        |
|-------------|--------------------|
| **GroupId** | `com.saucedemo`    |
| **ArtifactId** | `SeleniumTesting` |
| **Version**  | `1.0-SNAPSHOT`     |

- Click **Next**.

## **4. Set Project Name, Location, and JDK**
- **Project Name**: `SeleniumTesting`  
- **Project Location**: Choose a folder to save the project  
- **Project SDK / JDK**: Select a valid JDK (e.g., Java 17)  
- Click **Finish**.

## **5. Verify Project Structure**
The Maven project will have this structure:

- `src/main/java` → Your application code  
- `src/test/java` → Unit tests

## **6. Create a Java Class**
1. Right-click the package `com.saucedemo` in `src/main/java`.  
2. Select **New → Java Class**.  
3. Name it `App`.  


7. **Add Dependencies**:
   - Open the `pom.xml` file.
   - Add dependencies inside the `<dependencies>` tag:
     ```xml

     <dependencies>
      <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.12</version>
          <scope>test</scope>
      <dependency>
     </dependencies>
     ```

8. **Build the Project**:
   - Open the terminal within IntelliJ IDEA.
   - Navigate to the project directory:
     ```sh
     cd path/to/your/project
     ```
   - Run the build command:
     ```sh
     mvn clean install
     ```

### Manually Setting Up Maven

1. **Download Maven**:
   - Go to the [Maven download page](https://maven.apache.org/download.cgi).
   - Download the binary zip archive for your operating system.

2. **Extract Maven**:
   - Extract the downloaded archive to a directory of your choice.

3. **Set Up Environment Variables**:

##### macOS and Linux

1. **Open Terminal**: Open your terminal.
2. **Open Shell Configuration File**:
   - For Bash:
     ```sh
     nano ~/.bashrc
     ```
   - For Zsh:
     ```sh
     nano ~/.zshrc
     ```
3. **Add Environment Variables**:
   - Add the following lines to the file:
     ```sh
     export M2_HOME=/path/to/apache-maven
     export PATH=$M2_HOME/bin:$PATH
     ```
   - Replace `/path/to/apache-maven` with the path to the directory where you extracted Maven.
4. **Apply Changes**:
   - Save and close the file.
   - Apply the changes:
     ```sh
     source ~/.bashrc
     ```
     or
     ```sh
     source ~/.zshrc
     ```

##### Windows

1. **Open Environment Variables**:
   - Right-click on `This PC` or `Computer` on the desktop and select `Properties`.
   - Click on `Advanced system settings`.
   - Click on the `Environment Variables` button.
2. **Add `M2_HOME`**:
   - Click `New` under `System variables`.
   - Enter `M2_HOME` as the variable name and the path to your Maven directory as the variable value.
   - Click `OK`.
3. **Add Maven to `PATH`**:
   - Find the `Path` variable in the `System variables` section and select it.
   - Click `Edit`.
   - Add a new entry with the path to the Maven `bin` directory.
   - Click `OK`.

4. **Configure IntelliJ IDEA**:
   - Open IntelliJ IDEA.
   - Go to `File` > `Settings` > `Build, Execution, Deployment` > `Build Tools` > `Maven`.
   - Click on the `...` button next to the `Maven home directory` field.
   - Navigate to the directory where you extracted Maven and select it.
   - Click `OK` to save the changes.

## Gradle

### What is Gradle?

Gradle is a flexible build automation tool that supports multiple programming languages and platforms. It is widely used for Java and Android projects.

### Step-by-Step Guide

1. **Install Gradle**:
   - Follow the instructions in the [Configuration Guide](../course-requirements/course-reqs_section_01.md) to install Gradle.

2. **Create a Gradle Project**:
   - Open IntelliJ IDEA.
   - Go to `File` > `New` > `Project`.
   - Select `Gradle` and click `Next`.
   - Enter the project details and click `Finish`.

3. **Add Dependencies**:
   - Open the `build.gradle` file.
   - Add dependencies inside the `dependencies` block:
     ```groovy
     dependencies {
       testImplementation 'junit:junit:4.12'
     }
     ```

4. **Build the Project**:
   - Open the terminal within IntelliJ IDEA.
   - Navigate to the project directory:
     ```sh
     cd path/to/your/project
     ```
   - Run the build command:
     ```sh
     gradle build
     ```

### Manually Setting Up Gradle

1. **Download Gradle**:
   - Go to the [Gradle Releases](https://gradle.org/releases/) page.
   - Download the latest version of Gradle (binary-only distribution).

2. **Extract Gradle**:
   - Extract the downloaded zip file to a directory of your choice.

3. **Set Up Environment Variables**:

##### macOS and Linux

1. **Open Terminal**: Open your terminal.
2. **Open Shell Configuration File**:
   - For Bash:
     ```sh
     nano ~/.bashrc
     ```
   - For Zsh:
     ```sh
     nano ~/.zshrc
     ```
3. **Add Environment Variables**:
   - Add the following lines to the file:
     ```sh
     export GRADLE_HOME=/path/to/gradle
     export PATH=$GRADLE_HOME/bin:$PATH
     ```
   - Replace `/path/to/gradle` with the path to the directory where you extracted Gradle.
4. **Apply Changes**:
   - Save and close the file.
   - Apply the changes:
     ```sh
     source ~/.bashrc
     ```
     or
     ```sh
     source ~/.zshrc
     ```

##### Windows

1. **Open Environment Variables**:
   - Right-click on `This PC` or `Computer` on the desktop and select `Properties`.
   - Click on `Advanced system settings`.
   - Click on the `Environment Variables` button.
2. **Add `GRADLE_HOME`**:
   - Click `New` under `System variables`.
   - Enter `GRADLE_HOME` as the variable name and the path to your Gradle directory as the variable value.
   - Click `OK`.
3. **Add Gradle to `PATH`**:
   - Find the `Path` variable in the `System variables` section and select it.
   - Click `Edit`.
   - Add a new entry with the path to the Gradle `bin` directory.
   - Click `OK`.

4. **Configure IntelliJ IDEA**:
   - Open IntelliJ IDEA.
   - Go to `File` > `Settings` > `Build, Execution, Deployment` > `Build Tools` > `Gradle`.
   - Click on the `...` button next to the `Gradle home` field.
   - Navigate to the directory where you extracted Gradle and select it.
   - Click `OK` to save the changes.

## Ant

### What is Ant?

Ant is a Java-based build tool that uses XML to describe the build process and its dependencies. It is highly flexible and allows custom build processes.

### Step-by-Step Guide

1. **Install Ant**:
   - Follow the instructions in the [Configuration Guide](../course-requirements/course-reqs_section_01.md) to install Ant.

2. **Create a Build File**:
   - Create a `build.xml` file in the project directory.
   - Define the build process in the XML file:
     ```xml
     <project name="MyProject" default="compile">
       <target name="compile">
         <mkdir dir="build"/>
         <javac srcdir="src" destdir="build"/>
       </target>
     </project>
     ```

3. **Build the Project**:
   - Open the terminal within IntelliJ

-------

<div style="width: 100%">
<a href='environment-variables.md'><-- Previous Section: Environment Variables</a>
<div align="right"><a href='../5-ci-cd/index.md'>Proceed to Week 5 Session: Continuous Integration and Continuous Deployment--></a></div>
</div>
