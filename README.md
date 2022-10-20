# Steps

1) Deploy the first CloudFormation file
Supply your github username and personal access key so that you can connect to the internal Docker image (will be removed when the new public image is released)

2) upload all the files / folders in this repo (`conduktor-platform-config`, `buildspec.yml`, `Dockerfile`) in the S3 bucket that was created 

3) Launch a build in CodeBuild: this will build a Docker image with a proper configuration file to connect to an MSK cluster (this is fully serverless). To update the config, just change the file in S3 and relaunch a build in CodeBuild 

4) (optional) Start an MSK cluster (if none exist) using the second CloudFormation file

5) Deploy the third CloudFormation file, which will create an ECS service using Fargate, and launch an ALB to expose the conduktor platform container. Supply the bootstrap servers to the container (can be private)


# What if I have a license key?

In that case, change the task definition in the third CloudFormation file (will be going away soon as well, when 1.1.3 is released)

# Areas of improvement

- Join diagrams of architecture

- Output important information out of the CloudFormation files (ALB URL, etc)