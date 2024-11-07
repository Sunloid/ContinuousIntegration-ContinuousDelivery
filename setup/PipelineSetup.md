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