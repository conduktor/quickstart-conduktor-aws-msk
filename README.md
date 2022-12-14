# Steps

1) Deploy the first CloudFormation file, this will create ECR, S3 and CodeBuild resources

2) upload all the files / folders in this repo (`conduktor-platform-config`, `buildspec.yml`, `Dockerfile`) in the S3 bucket that was created 

3) Launch a build in CodeBuild: this will build a Docker image with a proper configuration file to connect to an MSK cluster (this is fully serverless). To update the config, just change the file in S3 and relaunch a build in CodeBuild 

![Base Setup](./arch-diagrams/step1-base.png)

4) (optional) Start an MSK cluster (if none exist) using the second CloudFormation file

5) Deploy the third CloudFormation file, which will create an ECS service using Fargate, and launch an ALB to expose the conduktor platform container. Supply the bootstrap servers to the container (can be private)

![Conduktor Platform ECS Service](./arch-diagrams/step3-ecs.png)
