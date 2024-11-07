# CI/CD Pipeline with Jenkins, Maven, SonarQube and Nexus on AWS EC2
This repository hosts a complete CI/CD pipeline designed for Java application utilizing Jenkins, Maven, SonarQube and Nexus on AWS EC2 instances. The pipeline automates build, test, quality analysis, and aritfact management to streamlien development workflows and maintain code quality in a scalable, cloud based environment. 

## Key Components 
- Jenkins: Orchestrates the CI/CD pipeline, automating each stage from build to deployment. 
- Maven: Manages dependencies, compiles code and builds the Java application. 
- SonarQube: Analyzes code quality, providing insights into code maintainability
- Nexus: Stores and manages built artifacts, ensuring version control and easy artifact retrieval.

## FEATURES
- Automated Builds and Tests: Maven handles dependency management and project builds, with integrated unit tests to ensure stability.
- Code Quality Analysis: SonarQube provides continuous feedback on code quality, allowing teams to address issues proactively.
- Artifact Management: Nexus stores versioned artifacts, making deployments consistent and traceable.
- Cloud Deployment: Entirely hosted on AWS EC2 instances, leveraging the cloud’s flexibility and scalability.

## Repository Structure
- Jenkinsfile: Defines the Jenkins pipeline stages, including build, test, analysis, and deployment.
- docs/: Contains architecture overview, and troubleshooting guides and working of the entire pipeline step by step.
- setup/: Contains setup of the different EC2 instances with their environments. 

## Getting Started
Refer to the README Quick Start for an overview and to docs/setup/ for detailed setup instructions for each component on AWS EC2. This setup is intended to be modular, making it adaptable to various environments and scalable as project needs grow.

