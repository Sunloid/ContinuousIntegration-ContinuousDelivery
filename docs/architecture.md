# Architecture of the Pipeline
The following information explains the stages of the pipeline which was written in code in the Jenkinsfile. 

## Stage 1. Fetch code
**git branch: 'main', url:'https://github.com/Sunloid/CICDtest'**:

This stage is responsinble for fetching code from the GitHub repository to the Jenkins application. The source file for this project is present in a seperate GitHub than the present one this was done for the simplicity of the source file as well the simplicity of this repository. Main the branch where the code is and url:'' indicates the URL of the source file repository. 

## Stage 2. Build
**sh 'mvn clean install -DskipTests'**:

This stage cleans the target repository and compiles the code into a .war or .jar file and stores it in a target repository. Breakdown of the command: 
- mvn clean install: This part is a Maven command that performs two main tasks:
  - clean: Deletes the target directory, which is where Maven stores compiled code and other build artifacts,       effectively cleaning up any files from previous builds.
  - install: Compiles the code, packages it (for example, into a .jar or .war file), and installs the artifact into the local Maven repository on your machine.
- -DskipTests: This flag tells Maven to skip running tests during the build process. It speeds up the build by not executing any test cases, which can be useful if you are confident the code is stable or if you're only interested in building the artifact itself. 

## Stage 3. Test
**sh 'mvn test'**:

As you can deduce from the code above this stage only responsible for testing the .war file made by the previous stage. This command is commonly used to verify that the code behaves as expected by running the unit and integration tests.

## Stage 4. Checkstyle Analysis
**sh 'mvn checkstyle:checkstyle'**:

The command sh 'mvn checkstyle:checkstyle' is used to run Checkstyle in a Maven project. Here’s what it does:
- mvn checkstyle:checkstyle: This Maven command calls the Checkstyle plugin to analyze the code for style and formatting issues based on a set of predefined or custom rules (often configured in a checkstyle.xml file).
- Checkstyle scans the source code and checks it against the coding standards defined in the configuration.
This command is useful for enforcing code quality and consistency across the codebase.

## Stage 5. Sonar Analysis
This stage is responsible for sending the project to the SonarQube analysis 

- **environment {scannerHome = tool 'sonar4.7'}**:
'sonar4.7' is the name of the SonarQube scanner in the ManageJenkins > Tools page. The makes sure that the scanner used by jenkins is infact sonarqube scanner. Be sure that the name of the sonarqube scanner in tools page is the same as the one over here. 

- **steps {withSonarQubeEnv('sonar') {.......}}**:
In the environment tab of the manage Jenkins the name of the SonarQube server needs to be sonar or anything else as the same as here. 
This part of the code makes multiple configuration's in the SonarQube server. It creates a new project with the name mentioned in this code (In this case FirstTest) if one is already not made. Defines the project version and the directory where the .war file will be present. It also configures the Java binaries in the SonarQube server. 

## Stage 6. Quality Gate
Responsible for taking the project through the quality gate in the SonarQube server which needs to manually created and setup first.

## Stage 7. UploadArtifact
Responsible for configuring and uploading a artifact to the Nexus repository

**nexusVersion: 'nexus3'**:
Mentions the Nexus version to the Jenkins server. 

**nexusUrl: '172.31.4.32:8081'**: 
This mentions the URL of the nexus server. This needs to be changed to the private IP address of the Nexus instance on EC2.

**repository: 'First-repo'**:
Mentions the repository where the artifact will be stores in Nexus. This repository needs to be manually made and named in the Nexus server. Keep in mind that the repository in the nexus server needs to be the same as the one mentioned here. 

**credentialsId: 'nexuslogin'**:
This mentions the ID of the nexus login credentials which are to be made manually in the Jenkins server. Again the ID needs to have the same name here as the one in the Jenkins server. 

**artifacts: [.....]**:
Mentions the name of the artifact which needs to be stored and also the directory where its present. 