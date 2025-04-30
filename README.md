
# Python Application with Jenkins CI/CD Pipeline 🚀

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/Jenkins.png" alt="Jenkins Logo">
</div>

## 1. Project Overview 📝

This project demonstrates a simple Python application with a complete CI/CD pipeline using Jenkins, Docker, and GitHub. The application provides a command-line tool that adds two numbers together, with automated testing and continuous integration/deployment.

> **Important**: Make sure Docker Desktop is running in the background before starting any Docker-related commands. ⚙️

## 2. Components 🧩

### Project Structure 📂
```
.
├── sources/
│   ├── add2vals.py      # Main application entry point
│   ├── calc.py          # Core calculation module
│   └── test_calc.py     # Unit tests
├── dist/               # Compiled executables
├── requirements.txt    # Python dependencies
├── Jenkinsfile        # Pipeline configuration
├── docker-compose.yml # Docker setup
└── README.md         # This documentation
```

### Python Application 🐍
- `add2vals.py`: Main application file that handles command-line arguments and displays results
- `calc.py`: Core calculation module containing the addition logic ➕
- `test_calc.py`: Test suite with unit tests for the calculation module 🧪
- `requirements.txt`: Python dependencies with specific versions 🧑‍💻

### Jenkins Pipeline ⚙️
- `Jenkinsfile`: Pipeline configuration defining the CI/CD workflow
- `docker-compose.yml`: Jenkins and agent setup with volume mappings and network configuration

### Docker Configuration 🐳
- Jenkins container: Main Jenkins server with persistent storage
- Jenkins agent container: For distributed builds
- Python build container: For building and testing the application

## 3. Steps to Perform This Project 🏁

### Step 1: Setup Jenkins 🛠️

1. Pull Jenkins image and start containers:
 ```bash
   docker-compose up -d
 ```

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss2.png" alt="Pull and start Jenkins">
</div>

2. Get initial admin password 🔑:
 ```bash
   docker-compose exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
 ```

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss3.png" alt="Get initial admin password">
</div>

3. Access Jenkins 🌐:
   - Open browser and go to `http://localhost:8080`
   - Enter the initial admin password from step 2

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss4.png" alt="Access Jenkins">
</div>

4. Install plugins 🔌:
   - Click "Install suggested plugins"
   - Wait for installation to complete

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss5.png" alt="Install plugins 1">

  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss6.png" alt="Install plugins 2">
</div>

5. Create first admin user 👤:
   - Enter your desired username
   - Enter your password
   - Enter your email
   - Click "Save and Continue"

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss7.png" alt="Create admin user">

  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss8.png" alt="Create admin user">
</div>

6. Configure Jenkins instance 🏗️:
   - Keep the default URL: `http://localhost:8080/`
   - Click "Save and Finish"

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss9.png" alt="Configure Jenkins 2">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss10.png" alt="Create pipeline 1">
</div>

7. Create Pipeline Project 🏗️:
   - Click "New Item"
   - Enter project name: `simple-python-pyinstaller-app`
   - Select "Pipeline"
   - Click "OK"
   - In pipeline configuration:
     - Scroll to "Pipeline" section
     - Select "Pipeline script from SCM"
     - Select "Git" as SCM
     - Enter repository URL: `https://github.com/Anugrah2334/Jenkins-Orchestration.git`
     - Enter branch specifier: `*/main`
     - Click "Save"

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss11.png" alt="Create pipeline 2">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss12.png" alt="Create pipeline 2">
</div>

8. Install and Configure Docker in Jenkins Container 🐳:
 ```bash
   # Install Docker
   docker-compose exec jenkins bash -c "apt-get update && apt-get install -y docker.io"
   
   # Start Docker service
   docker-compose exec jenkins bash -c "service docker start"
   
   # Verify Docker installation
   docker-compose exec jenkins docker --version
 ```

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss14.png" alt="Install Docker 1">

  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss15.png" alt="Install Docker 2">
</div>

9. Install Docker Plugins 🔧:
    - Go to "Manage Jenkins" > "Manage Plugins"
    - Click "Available" tab
    - Search for and install:
      - Docker Pipeline
      - Docker plugin
      - docker-build-step

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss16.png" alt="Install Docker plugins 1">

  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss18.png" alt="Install Docker plugins 2">
</div>

10. Sign in to Jenkins 🔑:
    - Use the credentials you created in step 5

<div align="center">
  <img src="https://github.com/Anugrah2334/Jenkins-Orchestration/blob/main/images/Screenshot22.png" alt="Sign in to Jenkins">
</div>

11. Run the Pipeline 🏃‍♂️:
    - Go to your pipeline project
    - Click "Build Now"

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss20.png" alt="Download executable 1">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss21.png" alt="Download executable 2">
</div>

### Step 2: Testing the Executable 🧪

1. Download the executable from Jenkins 📥:
   - Go to Jenkins dashboard
   - Click on `simple-python-pyinstaller-app`
   - Click on the latest build number
   - Look for "Build Artifacts" section
   - Click on `add2vals` to download it to your local machine

<div align="center">
  <img src="https://github.com/JANHVI-18/Jenkins_Orchestration/blob/main/images/ss23.png" alt="Download executable 4">
</div>

2. To run the Linux executable on Windows using WSL 🖥️:

```bash
   # Check if WSL is installed
   wsl --version
   # If WSL is not installed, you'll get an error
   # In that case, install WSL:
   wsl --install
   # After installation, restart your computer
   # Then open PowerShell and verify WSL is installed:
   wsl --version
```

---

## 4. What Does PyInstaller Do? 🔧

PyInstaller is used to create a standalone executable from the Python application. Here's how it works:

1. **Analysis Phase** 🔍
   - Analyzes `add2vals.py` and its dependencies
   - Identifies required Python files, libraries, and resources
   - Creates a dependency graph of the application

2. **Bundling Phase** 🛠️
   - Packages all identified dependencies
   - Includes Python interpreter
   - Bundles required libraries and resources
   - Creates a single executable file

3. **Output** 📤
   - Executable is created in the `dist` directory
   - Named `add2vals` (or `add2vals.exe` on Windows)
   - Contains everything needed to run the application

---

### Benefits of PyInstaller 🎉
1. **Portability** 🌍
   - Single executable file
   - No Python installation required
   - Easy distribution

2. **Dependency Management** 🔗
   -

 Automatically includes all dependencies (e.g., libraries)
   - Ensures no missing packages when running the executable

---

## 5. Final Remarks 📌

This project demonstrates how Jenkins can be integrated into a Python application to automate the build, test, and deployment process. Through Docker containers, we ensure that the environment remains consistent across all stages of the pipeline.

Now you're ready to run your Python app in an automated CI/CD environment with Jenkins! 🚀 Happy coding! 💻

