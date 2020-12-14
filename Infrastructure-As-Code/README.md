# Deploy a high availability web app using CloudFormation

**Problem:**

Your company is creating an Instagram clone called Udagram. Developers pushed the latest version of their code in a zip file located in a public S3 Bucket.

You have been tasked with deploying the application, along with the necessary supporting software into its matching infrastructure.

This needs to be done in an automated fashion so that the infrastructure can be discarded as soon as the testing team finishes their tests and gathers their results.

**Requirements:**

You'll need to create a Launch Configuration for your application servers in order to deploy four servers, two located in each of your private subnets. The launch configuration will be used by an auto-scaling group.

You'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, choose an Instance size and Machine Image (AMI) that best fits this spec. Be sure to allocate at least 10GB of disk space so that you don't run into issues.

Since you will be downloading the application archive from an S3 Bucket, you'll need to create an IAM Role that allows your instances to use the S3 Service.

Udagram communicates on the default HTTP Port: 80, so your servers will need this inbound port open since you will use it with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update its software.

The load balancer should allow all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound, it will only be using port 80 to reach the internal servers.

The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.

Files included in the project:

**cf_diagram.jpeg**: A diagram that acts as a visual aid for the CloudFormation script.

**network.yml**: This template deploys network components as outlined in the diagram.

**network-parameters.json**: In this file, parameter values are provided for the parameter keys in network.yml.

**servers.yml**: This template deploys the security group, web app load balancer and defines IAM roles to fetch required files from the S3 bucket. Further, it deploys the web application on the web server.

**server-parameters.json**: In this file, parameter values are provided for the parameter keys in servers.yml.

**create.sh**: A bash script that accepts the name of the cloudformation stack, template body and parameters file to create a CloudFormation stack.

**update.sh**: A bash script that accepts the name of the cloudformation stack, template body and parameters file to update an existing CloudFormation stack.

**delete.sh**: A bash script that accepts the name of the cloudformation stack to delete an existing CloudFormation stack.

**output.png**: A screenshot of the Web App in action.

[References to documentation are provided in .yml files.]
