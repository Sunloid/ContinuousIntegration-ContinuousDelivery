# Complete Pipeline Setup
This file contains step by step all instructions on how to setup up this pipeline. The main components needed are: 

- AWS: Amazon Elastic Compute Cloud (EC2) is a web service from Amazon Web Services (AWS) that provides cloud-based compute capacity that can be resized. EC2 allows users to run applications on the public cloud by provisioning virtual servers, or EC2 instances, within the AWS cloud. 
- GitHub: GitHub is a web-based platform that allows users to store, share, and collaborate on code
- Jenkins: Jenkins is a popular open-source tool used for continuous integration (CI) and continuous delivery (CD)  
- Maven: Maven is an open-source build automation and project management tool that is primarily used for Java development.
- Nexus: Nexus is a tool that stores, organizes, and distributes artifacts for development. It's built by Sonatype and is commonly used to host Apache Maven. Developers can use Nexus to control access to and deploy artifacts from a single location.
- SonarQube: SonarQube is an open-source platform that helps developers and teams improve the quality of their code by analyzing it for bugs, vulnerabilities, and other issues

## AWS SETUP
1. **Security Groups:**
    - Jenkins: 
        ![Alt text](<image (2).png>)
    - SonarQube:
        ![Alt text](<image (3).png>) 
    - Nexus: 
        ![Alt text](<image (4).png>)

2. **Jenkins Instance Setup:** 
    - Create a EC2 instance with the name of Jenkins server.
    - Give it the Jenkins security group which you just made.
    - Use Ubuntu linux as the base image.
    - For instance type use t2.medium 
    ![Alt text](<image (5).png>)
    - Click on advanced details and in the user data section copy paste the code from the install_jenkins.sh file  
    ![Alt text](<image (6).png>)
    - Launch the instance. 

3. **SonarQube Instance Setup:**
    - Create a EC2 instance with the name of SonarQube server. 
    - Give it the SonarQube security group which you just made. 
    - Use ubuntu Linux as the base image.
    - For instance type use t2.medium  
    ![Alt text](<image (7).png>)
    - Click on advanced details and in the user data section copy paste the code fom the install_SonarQube.sh file
    ![Alt text](<image (8).png>)
    - Launch the instance. 

4. **Nexus Instance Setup:**
     - Create a EC2 instance with the name of Nexus server. 
     - Give it the Nexus security group which you just made. 
     - Use ubuntu linux as the base image. 
     - For instance type use t2.medium. 
     ![Alt text](<image (9).png>)
     - Launch the instance. 
     - Now connnect to the EC2 instance via ssh and use the instruction in the install_Nexus.sh file to complete the setup. 

## Jenkins Server Setup    
- Connect to the Jenkins Instance and run the command: sudo systemctl status jenkins
- The secret key to the jenkins server will be present copy it 
- Now use the public IP address of the jenkins along with the port to reach the Jenkins server and Install the suggested plugins. 
- Go to managae Jenkins install the following plugins: Pipeline stage view, Nexus artifact uploader, Sonarqube scanner, Pipeline maven Integration, pipeline utility step and Build Timestamp and install without restart
- Go to manage Jenkins > Tools and add the following details: 
    1. OracleJDK8 Installation:
        ![Alt text](<image (10).png>)
    2. Apache Maven Installation: 
        ![Alt text](<image (11).png>)
    3. SonarQube Installation:    
        ![Alt text](<image (12).png>)
- Now go Manage Jenkins > Credentials and add credentials
    1. Nexus:
    ![Alt text](<image (13).png>)
    2. SonarQube: For SonarQube go to sonarqube server login with username and password (admin) then account > security and Generate a token. Copy the token and come back to Jenkins server and make a new credentials with the generated token. 
    ![Alt text](<image (14).png>)

## SonarQube Server Setup 
    - There is not much setup to do in sonarqube server. 
    - Go to quality gates on the top bar and press create. 
    - Give it the name Bugs-100 
    - Add condtion of bugs with the value of 100. 
    - There will be more things to do in sonarqube once the jenkins build is run. 

## Nexus Server Setup 
    - Launch the server and complete the login with the instructions shown on the screen. 
    - Click on setting icon on the top bar and then the create repository button. 
    - Choose maven2 (hosted)
    - Give the repository the name 'First-repo'
    - save 
