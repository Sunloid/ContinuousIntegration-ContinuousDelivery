# Architecture of the Pipeline
The following information explains the stages of the pipeline which was written in code in the Jenkinsfile. 

## Stage 1. Fetch code:
**git branch: 'main', url:'https://github.com/Sunloid/CICDtest'**

This stage is responsinble for fetching code from the GitHub repository to the Jenkins application. The source file for this project is present in a seperate GitHub than the present one this was done for the simplicity of the source file as well the simplicity of this repository. Main the branch where the code is and url:'' indicates the URL of the source file repository. 

## Stage 2. Build: 
**sh 'mvn clean install -DskipTests'**

This stage cleans the target repository and compiles the code into a .war or .jar file and stores it in a target repository. Breakdown of the command: 
- mvn clean install: This part is a Maven command that performs two main tasks:
  - clean: Deletes the target directory, which is where Maven stores compiled code and other build artifacts,       effectively cleaning up any files from previous builds.
  - install: Compiles the code, packages it (for example, into a .jar or .war file), and installs the artifact into the local Maven repository on your machine.
- -DskipTests: This flag tells Maven to skip running tests during the build process. It speeds up the build by not executing any test cases, which can be useful if you are confident the code is stable or if you're only interested in building the artifact itself. 

# Stage 3. Test: 

