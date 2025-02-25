# BaseRock AI

- BaseRock.ai is an advanced AI-driven platform that transforms the landscape of software development through automated unit test generation. Its main features include exceptional code integrity assurance, fast and responsive test generation, and personalized code feedback to improve overall code quality. For software engineers, it expedites the development cycle, enhances code reliability, and offers valuable insights for code refinement.   

- Website: [https://www.baserock.ai](http://baserock.ai/)

# Guidelines for Java Projects

## Libraries required by BaseRock Plugin

In order to ensure successful test generation, the BaseRock Plugin mandates the presence of JUnit, Mockito, and Hamcrest libraries as dependencies in the source project.

Below are the steps to seamlessly integrate these dependencies into your project:

## Junit Platform

BaseRock facilitates unit test generation across JUnit 5, JUnit 4, or TestNG platforms. The tool automatically identifies the JUnit version by inspecting the unit testing libraries declared in the project. If the project doesn't currently employ any unit testing libraries, it's necessary to include one of these libraries to enable seamless integration with BaseRock. If the project contains multiple JUnit libraries (e.g., JUnit 4 and TestNG), users have the option to set their preferred platform in the settings.



JUnit 5 introduced the concept of the JUnit Platform, which is a new foundation for running testing frameworks on the Java Virtual Machine (JVM). The JUnit Platform provides an execution environment for running tests and supports the creation of new testing frameworks. The JUnit Platform also introduced the concept of the JUnit Platform Launcher, which is responsible for discovering and executing tests on the platform.

The JUnit Platform supports different testing frameworks, and the term "engine" is often used to describe the individual components responsible for running tests written in a particular framework. For example:

JUnit Jupiter Engine: The engine that runs tests written using the JUnit Jupiter programming model.

JUnit Vintage Engine: The engine that runs tests written in JUnit 3 and JUnit 4 style.

## Junit 5 Platform
BaseRock utilizes the JUnit Jupiter programming model for test code generation and employs the respective engine to execute and validate the tests if Junit 5 libraries have been included in the project. Following dependencies can be included for JUnit 5:

- Maven 
   
   ```
      <dependency>
         <groupId>org.junit.jupiter</groupId>
         <artifactId>junit-jupiter-api</artifactId>
         <version>5.9.2</version>
         <scope>test</scope>
      </dependency>
      
       <dependency>
         <groupId>org.junit.jupiter</groupId>
         <artifactId>junit-jupiter-engine</artifactId>
         <version>5.9.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.junit.jupiter', name: 'junit-jupiter-api', version: '5.9.2'
       testRuntimeOnly group: 'org.junit.jupiter', name: 'junit-jupiter-engine', version: '5.9.2'
 ```

 
## Junit 4 Platform

BaseRock utilizes the JUnit 4 Vintage programming model for test code generation and employs the respective engine to execute and validate the tests if Junit 4 libraries have been included in the project. Following dependencies can be included for JUnit 4:

- Maven 
   
   ```
      <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.13.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'junit', name: 'junit', version: '4.13.2'
 ```

## TestNG Platform

BaseRock utilizes the TestNG programming model for test code generation and employs the respective engine to execute and validate the tests if TestNG libraries have been included in the project.

For Java version 11 and higher:
- Maven

   ```
      <dependency>
         <groupId>org.testng</groupId>
         <artifactId>testng</artifactId>
         <version>7.9.0</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle

	``` 
       testImplementation group: 'org.testng', name: 'testng', version: '7.9.0'
	```
For Java Versions less than 11
- Maven

   ```
      <dependency>
         <groupId>org.testng</groupId>
         <artifactId>testng</artifactId>
         <version>7.5</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle
	
	``` 
       testImplementation group: 'org.testng', name: 'testng', version: '7.5'
	```

## Mockito Libraries ( JDK 11 and Above : 5.x)

Mockito is a library designed for creating mocks and stubs of objects, enabling isolation across logical layers in the code. To ensure compatibility with Java 11 or newer versions, it is recommended to use Mockito version 5.x or later.

For JDK 21, 22 (recommended mockito version 5.7.0, we need byte-buddy that is equal to or above 1.14.9 and so we exclude the byte-buddy that is shipped with mockito-inline)
For JDK 23 (recommended mockito version 5.7.0, we need byte-buddy that is equal to or above 1.14.16 and so we exclude the byte-buddy that is shipped with mockito-inline)

- Maven for JDK 23

   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.7.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
    	 <exclusions>
            <exclusion>
               <groupId>net.bytebuddy</groupId>
               <artifactId>byte-buddy</artifactId>
            </exclusion>
    	 </exclusions>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.14.16 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.16</version>
         <scope>test</scope>
      </dependency>
  ```

- Maven for JDK 21, 22

   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.7.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
    	 <exclusions>
            <exclusion>
               <groupId>net.bytebuddy</groupId>
               <artifactId>byte-buddy</artifactId>
            </exclusion>
    	 </exclusions>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.14.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.9</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle for JDK 23

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.7.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'{
		exclude group: 'net.bytebuddy', module: 'byte-buddy
	}
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.14.16
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.16'
 ```

- Gradle for JDK 21, 22

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.7.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'{
		exclude group: 'net.bytebuddy', module: 'byte-buddy
	}
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.14.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.9'
 ```

For JDK 11 to JDK 20  (recommended mockito version 5.2.0)

- Maven 
   
   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>5.2.0</version>
         <scope>test</scope>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.12.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.4</version>
         <scope>test</scope>
      </dependency>
  ```

- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '5.2.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '5.2.0'
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.12.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.4'
 ```

## Mockito Libraries ( JDK 8 : 4.x (recommended 4.11.0) )

Mockito is a library designed for creating mocks and stubs of objects, enabling isolation across logical layers in the code. To ensure compatibility with Java 8 version, it is recommended to use Mockito version 4.x or older.
- Maven 
   
   ```
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-core</artifactId>
         <version>4.11.0</version>
         <scope>test</scope>
      </dependency>
      
      <dependency>
         <groupId>org.mockito</groupId>
         <artifactId>mockito-inline</artifactId>
         <version>4.11.0</version>
         <scope>test</scope>
      </dependency>

      <!-- byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. 
        We need at least 1.12.9 -->
      <dependency>
         <groupId>net.bytebuddy</groupId>
         <artifactId>byte-buddy</artifactId>
         <version>1.14.4</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.mockito', name: 'mockito-core', version: '4.11.0'
       testImplementation group: 'org.mockito', name: 'mockito-inline', version: '4.11.0'
       // byte-buddy is an optional dependency. Mockito brings it, but an old version can cause problems. We need at least 1.12.9
       testImplementation group: 'net.bytebuddy', name: 'byte-buddy', version: '1.14.4'
 ```


## Hamcrest Library  
It brings substantial enhancements in terms of readability, expressiveness, composability, and error message reporting. For a detailed exploration of these advantages, you can refer to our blog post at: [Understanding Hamcrest: Advantages and Disadvantages for Java Testing](https://www.baserock.ai/blog/understanding-hamcrest-advantages-and-disadvantages-for-java-testing).

- Maven 
   
   ```
      <dependency>
         <groupId>org.hamcrest</groupId>
         <artifactId>hamcrest</artifactId>
         <version>2.2</version>
         <scope>test</scope>
      </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation group: 'org.hamcrest', name: 'hamcrest', version: '2.2'
 ```

## Spring boot Test Library  
Spring Boot provides a number of utilities and annotations to help when testing your application.

- Maven 
   
   ```
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-test</artifactId>
      <version>3.3.5</version>
      <scope>test</scope>
      <exclusions>
        <exclusion>
          <groupId>org.junit.jupiter</groupId>
          <artifactId>junit-jupiter</artifactId>
        </exclusion>
        <exclusion>
          <groupId>org.mockito</groupId>
          <artifactId>mockito-core</artifactId>
        </exclusion>
        <exclusion>
          <groupId>org.mockito</groupId>
          <artifactId>mockito-junit-jupiter</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
  ```
  
- Gradle

 ``` 
       testImplementation('org.springframework.boot:spring-boot-starter-test') {
        exclude group: "org.junit.jupiter", module: "junit-jupiter"
        exclude group: "org.mockito", module: "mockito-core"
        exclude group: "org.mockito", module: "mockito-junit-jupiter"
    }
 ```

## OS Libraries

- Linux

BaseRock AI Test Coder requires libgcc and libstdc++6 to be installed on linux before using the plugin. Please make sure these two packages are installed in your machine. For Ubuntu distribution you could install executing the following commands: 
 ``` 
   sudo apt install libgcc-s1
   sudo apt install libstdc++6
 ```

## Composable tests

### Running Composable Tests with BaseRock.AI

To execute composable tests, our engine leverages built-in tasks provided by Android projects. To ensure smooth test execution, it's important to verify that your Gradle project is correctly configured.

### Verifying Your Project Configuration

Run the following commands to check if your project is properly configured:

 ``` 
./gradlew build
./gradlew :app:connectedDebugAndroidTest
 ``` 

If these commands execute without errors, your project is ready to run composable tests.

### Test Location

Regular unit tests are generated in the test folder. Composable tests are generated in the androidTest folder.

### Packaging options

When building an Android app, the packaging process merges resources and metadata from all libraries and dependencies into a single APK or AAB file. If multiple libraries include files with the same name and path (such as license files in the META-INF directory), this causes a conflict because the Android packaging system does not allow duplicate files. To resolve this, you need to use packagingOptions in your build.gradle to exclude these duplicate files. This ensures the build process completes successfully without including unnecessary metadata, which is typically not required for your app's runtime functionality.

#### (AGP < 8.0):

``` 
android {
    packagingOptions {
        exclude "META-INF/licenses/**"
        exclude "META-INF/AL2.0"
        exclude "META-INF/LGPL2.1"
        exclude "META-INF/LICENSE.md"
        exclude "META-INF/LICENSE"
        exclude "META-INF/LICENSE-notice.md"
        exclude "META-INF/NOTICE"
        exclude "META-INF/*.md"
        exclude "META-INF/DEPENDENCIE"
    }
}

``` 

#### (AGP 8.0 and above):

``` 
android {
    packaging {
        resources {
            excludes += [
                "META-INF/licenses/**",
                "META-INF/AL2.0",
                "META-INF/LGPL2.1",
                "META-INF/LICENSE.md",
                "META-INF/LICENSE",
                "META-INF/LICENSE-notice.md",
                "META-INF/NOTICE",
                "META-INF/*.md",
                "META-INF/DEPENDENCIE"
            ]
        }
    }
}
``` 

Please assure you packaging options are fine, so our plugin will be able to execute the tests.

### Enabling Coverage for BaseRock.AI Test Generation

To enable test coverage collection when using BaseRock.AI to generate composable tests, you need to configure your Gradle build file. Specifically, you must enable the testCoverageEnabled property in the debug build type.

Add the following snippet to your build.gradle file:

#### (AGP < 8.3):

``` 
android {
    buildTypes {
        debug {
            testCoverageEnabled true
        }
    }
}
``` 

#### (AGP 8.3 and above):
``` 
android {
    buildTypes {
        debug {
            enableUnitTestCoverage = true
            enableAndroidTestCoverage = true
        }
    }
}
``` 


Once this property is set, BaseRock.AI will collect test coverage data while generating tests, allowing you to measure and optimize your test coverage effectively.

## Java Version Requirement
BaseRock supports unit test generation for project using Java Version 8 to 17 without any adjustments. However for Java 18 or later versions, configuring Intellij IDEA is required to boot up with the respective versions, as described below.

### Supporting projects with a java version 18 or later
The current IntelliJ version (2024.1) defaults to boot up with Java 17, which may limit plugins' ability to interpret and process classes generated using Java 18 or later versions. 

Please follow below instructions to update the Java Runtime in IntelliJ.

	- In the main menu, go to Help | Find Action
	- Find and select the Choose Boot Java Runtime for the IDE action.
	- Select the new desired runtime ex: JetBrains Runtime JBR (vanilla).
	- Click OK.
	- If necessary, you can change the location where IntelliJ IDEA will download the selected runtime.
	- Wait for IntelliJ IDEA to restart with the new runtime.
	- This adjustment should help mitigate the JVM crash issue until the official fix is released.

![alt text](https://github.com/Sapient-AI/docs/blob/main/images/choose-boot-java-runtime-for-ide.png?raw=true)

Intellij's Official documentation available here [official guide](https://www.jetbrains.com/help/idea/switching-boot-jdk.html) to change the default Java version for IntelliJ boot-up.

### Fixing Java Version

Following steps are required to fix the java version in the project:

- Gradle
 ```
 java {
    sourceCompatibility = JavaVersion.<VERSION>
    targetCompatibility = JavaVersion.<VERSION>
}
 ```

- Maven
 ```
      <properties>
         <maven.compiler.source><VERSION></maven.compiler.source>
         <maven.compiler.target><VERSION></maven.compiler.target>
      </properties>
 ```

 
## Cyclomatic Complexity
  
The cyclomatic complexity of a section of source code is a quantitative measure indicating the number of linearly independent paths within it. This metric is derived by constructing a Control Flow Graph of the code, effectively quantifying the number of linearly independent paths through a given program module. It's labeled as LOW, MEDIUM or HIGH based on number of independent paths.

- LOW 
   No. of independent paths is less than or equal to 7.

- MEDIUM
   No. of independent paths is between 7 and 10.

- HIGH 
   No. of independent paths is greater than 10.


## Disabled Generated Tests

When a method under test involves system calls, there's a potential for adverse effects such as program termination, thread hang, or file/directory deletion. To mitigate risks, we identify and flag such potentially harmful calls by adding @Disabled to the generated test. By default, these tests won't be executed. Users are encouraged to review test details and may choose to remove @Disabled if they determine the test is safe.

For example, the test generated may look like this:
 ```
    //Sapient generated method id: ${3f698e62-d52c-38cd-bce6-39784a59918a}
    @Disabled(value = "Potential harmful system call (System.exit) detected; Learn more: https://github.com/Sapient-AI/docs#disabled-test-due-to")
    @Test()
    void myMethodWhenParam() {
        /* Branches:
         * (param) : true
         */
        TestSystemExit target = new TestSystemExit();
        String result = target.myMethod(true);
        assertAll("result", () -> assertThat(result, equalTo("!")));
    }
 ```


The following Java functions are considered potentially dangerous, and if detected during test generation, @Disabled will be added to the test.

- Regular Functions:
	- java.lang.Runtime: exec, exit, halt, wait
	- java.lang.Thread: destroy, interrupt, run, start, stop, suspend, wait
	- java.net.ServerSocket: accept, bind
	- java.nio.channels.Selector: (all functions)
	- java.util.concurrent.CompletableFuture: complete, completeAsync
	- java.util.concurrent.CountDownLatch: await, countDown
	- java.util.concurrent.CyclicBarrier: await
	- java.util.concurrent.ExecutorService: awaitTermination, invokeAll, invokeAny, shutdown, shutdownNow, submit
	- java.util.concurrent.Future: get

- Static Functions:
	- java.nio.file.Files: delete, deleteIfExists
	- java.lang.System: exit

## Batch Generation
BaseRock offers a robust feature enabling the specification of one or multiple source folders for unit test code generation. These folders yield numerous classes, each of which is meticulously analyzed and processed to generate test code. BaseRock methodically examines every method within these classes, compiling a comprehensive list of test cases and associating them with their respective test methods. Notably, certain methods, such as main methods for launching applications or getters/setters for data access, are purposefully excluded. This ensures that unit test code generation remains focused on functional code and avoids unnecessary code sprawl.


### Main Method

Main method is used to launch Java application, start server or setup infrastructure elements, so it has been excluded from unit testing.

### Getters and Setters Methods

Getters and Setters are standard methods used to maintain the state in a Java class. These are devoid of programming complexity, so they have been excluded from unit testing.

### Equals, hashCode, wait, notify, waitAll, notifyAll etc.

Common object methods such as equals, hashCode, wait, notify, waitAll, notifyAll etc. are excluded from unit testing.


## Troubleshooting

### Byte buddy minimal version

If you face the following issue when running the tests, please make sure the version of  byte-buddy is **1.12.9** or later
 ```
    Could not initialize plugin: interface org.mockito.plugins.MockMaker
    Caused by: org.mockito.exceptions.base.MockitoInitializationException:
    It seems like you are running Mockito with an incomplete or inconsistent class path. Byte Buddy could not be loaded.
    Byte Buddy is available on Maven Central as 'net.bytebuddy:byte-buddy' with the module name 'net.bytebuddy'.
```   

### Crashing Intellij build version 233 (2023.3) and Jetbrains Runtime 17 with JCFE

Some IntelliJ users have encountered JVM crashes when using IntelliJ 2023.3 with JetBrains 17 and JCFE, which is the default option upon installing an IntelliJ version, as reported here [IDEA-340379](https://youtrack.jetbrains.com/issue/IDEA-340379/JVM-crash-after-IDE-upgrade-with-shared-indexes-SIGSEGV-in-AppendOnlyLogOverMMappedFileRecordLayout.readHeader).

JetBrains has already acknowledged and scheduled to release the fix in the 2024 release. Till then, users are recommended to change the JRE that IntelliJ uses from the version with JCFE to the vanilla version. 

Please refer to instructions mentioned in section [Supporting projects with a java version 18 or later](#Supporting-projects-with-a-java-version-18-or-later)

### Unable to update build.gradle/build.gradle.kts/pom.xml

In case of a message like `Unable to update build.gradle.kts. Please update with these instructions` we are usually not able to find the build files because of: 
- Either it is missing in the package.
- It is renamed.
To resolve it please follow along the doc to add these dependencies to your build file. After a successful sync, the plugin will start generating tests for your repository. 

# Guidelines for Python Projects

## Requirements

To ensure the proper functioning of the BaseRock AI VS Code extension, please ensure the following requirements are met:

* Python >= 3.8: Ensure you have Python version 3.8 or higher installed.

* VS Code Python Extension: Install the official Python extension by Microsoft to enable VS Code to detect Python projects.

* Virtual Environment (Recommended): It is highly recommended to set up a virtual environment and install project dependencies within it.

If you encounter any errors while setting up the environment, follow these steps:

## Ensure Python is Installed and Accessible

* Run `python3 --version` to verify the installation.
* Ensure Python is added to the system PATH.

## Check Virtual Environment Setup

* Run `python3 -m venv .venv` to create a virtual environment.
* Activate the virtual environment using:
    * **Windows**: `.venv\Scripts\activate`
    * **Mac/Linux**: `source .venv/bin/activate`
* Install dependencies: `pip install -r requirements.txt`

## Review the Output Panel in VS Code

* Open the **Output** panel (`View -> Output` in VS Code) to check error messages.

## Restart VS Code and Retry Setup

* Close and reopen VS Code after making changes.
* Retry running the environment setup.

## Additional Help

If you continue to experience issues after following these steps, please:

1. Ensure all system requirements are met
2. Check your Python version compatibility
3. Verify all required dependencies are installed
4. Contact support with detailed error messages if problems persist

## Common Issues and Solutions

### Python Not Found
```bash
# Add Python to PATH (Windows)
# Add to Environment Variables -> System Variables -> Path:
C:\Users\YourUsername\AppData\Local\Programs\Python\Python3x\
C:\Users\YourUsername\AppData\Local\Programs\Python\Python3x\Scripts\

# Add Python to PATH (MacOS)
# zsh - default shell for macOS Catalina and later
echo 'export PATH="/usr/local/bin:/usr/local/opt/Python3x/libexec/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Virtual Environment Activation Fails
```bash
# Windows PowerShell may need to run:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Try alternative activation on Windows:
.\.venv\Scripts\activate.bat
```

Remember to replace `Python3x` with your specific Python version number.

# Guidelines for JavaScript & TypeScript Projects

## **Prerequisites**

Before using the BaseRock AI VS Code extension, ensure the following requirements are met:

### **1. Testing Framework Configuration**
- Your project must include a **testing framework** (e.g., Jest, Mocha) and an **assertion library** (e.g., Chai, Expect) as **dev dependencies** in `package.json`.
- Example (`package.json`):
  ```json
  "devDependencies": {
    "jest": "^29.0.0",
    "chai": "^4.3.0"
  }
  ```

### **2. Test File Configuration**
- Ensure your test files are located in a directory that matches the test regex pattern set in your configuration files.
- Example regex for Jest:
  ```json
  {
    "testMatch": ["**/__tests__/**/*.[jt]s?(x)"]
  }
  ```
- If test files are not detected, check if they conform to your **configured pattern**. You can also update the location of your test file in BaseRock Settings

### **3. Framework-Specific Requirements**
Depending on your project type, install the required testing utilities:
- **React**: Ensure `@testing-library/react` is installed.
  ```json
  "devDependencies": {
    "@testing-library/react": "^13.4.0"
  }
  ```
- **Angular**: Ensure `@angular/core/testing` is listed in your dependencies.
  ```json
  "devDependencies": {
    "@angular/core": "^15.0.0"
  }
  ```

### **4. Install Dependencies**
- Run the appropriate package manager command based on your project setup:
  ```sh
  # Using npm
  npm install  

  # Using yarn
  yarn install
  ```

## **Troubleshooting**

### **Unable to Sign In?**

If you are experiencing issues signing in, follow these steps:

1. When the **Sign In** prompt appears at the bottom right of VS Code, click **Proceed**.
2. This will open your default browser, where you can select a preferred sign-in method.
3. For the best experience, use **Google Chrome** or **Mozilla Firefox**.
- If a different browser opens automatically, **copy the URL** and paste it into Chrome or Firefox to proceed.

### **Test Generation Issues**
**1. Verify Testing Framework Installation**
- Run:
  ```sh
  npx jest --version  # For Jest  
  npx mocha --version # For Mocha  
  ```
- If not found, install one.

**2. Verify test file location**
- Ensure test files are in a recognized test folder.
- Check your test file regex configuration.

**3. Ensure VS Code has access to the workspace**
- If you see permission errors, restart VS Code and check workspace settings.

### **Tests Execution Issues**
**1. Confirm that the test runner is working**
- Try running tests manually:
  ```sh
  npm test path/to/testfile.js
  ```
- If tests fail, check for missing dependencies.

**2. Check `testCommand` configuration**
- Ensure that the test command mentioned in Output > BaseRock AI is correct. If not, update it in BaseRock settings.

### **BaseRock Settings**

- Ensure BaseRock settings has the correct configurations required to generate & execute the tests.
- BaseRock settings can be accessed by clicking on the baserock logo on the sidebar (left-most panel) and the clicking on settings icon on the top right.
- Following images can be used as a guide to save baserock settings.
- ![BaseRock Sidebar](images/vscode/baserock_sidebar.png)
- ![BaseRock Settings](images/vscode/baserock_settings.png)
- ![BaseRock Settings Saved](images/vscode/baserock_settings_saved.png)

### **CodeLens Implementation**
**1. Ensure file type is supported**
- CodeLens appears only for **JavaScript/TypeScript test files** (`.js`, `.ts`, `.jsx`, `.tsx`, `.vue`).

**2. Check VS Code settings**
- Ensure `editor.codeLens` is enabled in your settings (`Ctrl + ,` → Search `CodeLens`).

### **BaseRock with Cursor IDE**
BaseRock plugin can be installed with cursor IDE. The minimum version for the support is `0.45.14`.

---

### **Support**
For additional assistance, please contact our support team:
- Email: support@baserock.ai


