# Working of the Pipeline 
- Assuming that the pipeline setup is complete step by step from the PipelineSetup.md now you need to create a Job in jenkins with the item type as pipeline and give it any name. 
![Alt text](<x1.png>)
- Paste the Jenkinsfile in the pipeline space 
![Alt text](<x2.png>)
- Apply and Save.

## SonarQube Webhooks
- Build the Jenkins pipeline and abort the pipeline when it reaches the quality gate stage. 
- Go to SonarQube Projects > FirstTest > Project Setting > Webhooks 
![Alt text](<x3.png>)
- Use the Jenkins Public IP address for the above. 
- Save and build the pipeline again in the Jenkins server. 

The Pipeline works after 7 tries lmao.
![Alt text](<x4.png>)