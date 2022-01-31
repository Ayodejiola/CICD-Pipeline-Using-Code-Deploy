# aws_code_deploy
## Steps for AWS code deploy using S3 as source
 1.  **Create IAM Roles - CodeDeploy & EC2CodeDeploy**
 1.  **Create EC2 instance with the following software packages should install**<br/>
 1.  **Choose AMI: Amazon Linux 2**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/AMI.png)<br/>
 1.  **Choose AMI role as EC2CodeDeploy**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/ConfigureInstance.png)<br/>
 1.  **Choose User Data: for installing required packages.**<br/>
     #!/bin/bash<br/>
     sudo yum -y update<br/>
     sudo yum -y install ruby<br/>
     sudo yum -y install wget<br/>
     cd /home/ec2-user<br/>
     wget https://aws-codedeploy-ap-south-1.s3.ap-south-1.amazonaws.com/latest/install<br/>
     sudo chmod +x ./install<br/>
     sudo ./install auto<br/>
     sudo yum install -y python-pip<br/>
     sudo pip install awscli<br/>

     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/UserData.png)<br/>
 1.  **Security groups: which enable port SSH port 22 and HTTP 80 for application**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/configureSecutiryGroup.png)<br/>     
 1.  **Add tags to your EC2 instance**<br/>
     ![alt text](https://github.com/prabhakar2020/aws_code_deploy/blob/master/addTags.png)<br/>
 1.  **Launch instance**<br/>
 1.  9.	Create Pipeline, add source(Github) and skip build stage
![image](https://user-images.githubusercontent.com/97601366/151829161-41d298e9-7c70-447c-a3db-4d9936a8980a.png)


11.	Create a DeploymentGroup
12.	This completes Pipeline.
13.	View application by hitting the DNS of the ec2 instance
14.	Each time a new change is made to the Source code on the repo, the pipeline is triggered, and the deployment is updated.

