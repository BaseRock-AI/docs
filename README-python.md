# BaseRock AI Environment Setup Troubleshooting Guide

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

## Windows-Specific Python Setup

Before running on Windows, follow these steps:

1. Install the Python 3.13 interpreter from Microsoft Store:
   * Visit [Python 3.13 in Microsoft Store](https://apps.microsoft.com/detail/9NRWMJP3717K)
   * Click "Get" or "Install" to download and install Python 3.13

2. Select the Python 3.13 interpreter in VS Code:
   * Open VS Code
   * Press `Ctrl+Shift+P` to open the command palette
   * Type "Python: Select Interpreter" and select it
   * Choose the Python 3.13 interpreter from the list

3. Open a new terminal in VS Code to ensure it uses the selected Python interpreter

This approach ensures you're using the Microsoft Store version of Python, which is properly integrated with Windows and easier to maintain.