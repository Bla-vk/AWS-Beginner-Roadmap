<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy a Web App with CodeDeploy

**Project Link:** [View Project](https://nextwork.ai/projects/836cda66-f725-5082-bdb3-0152b1d7a61b)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-27)

## Introducing Today's Project!

In this project, I will demonstrate the use of CodeDeploy to deploy an app. I'm doing this project to learn about deployment (taking code from a development environment to a live environment), and how it can be automated using a combination of CodeDeploy and deployment scripts.

### Key tools and concepts

The services we used included CodeDeploy, CodeBuild, CodeArtifact, IAM, CloudFormation, EC2, S3, CodeConnections, VS Code, and GitHub. Key concepts we learnt included deployments, deployment groups, deployment scripts, and appspec.yml, along with the importance of rebuilding your project before deploying and why deployment recovery matters in production environment.

### Project reflection

This project took me approximately 3 hours, including troubleshooting and documentation time. The most challenging part was running into a Deploy failed error with CodeDeploy when attempting the disaster recovery step. However, once I restarted the process and cleared the conflicting file via a direct SSH connection to my deployment EC2 instance, it worked the second time. It was most rewarding to see the deployed web app live.

This project is part five of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

## Deployment Environment

To set up for CodeDeploy, I launched an EC2 instance and a VPC, which together form the production environment. I need to separate the development environment (where the code is written) from the production environment (where the web app is deployed) so that code developers are working on doesn't get shown to users until it's ready to be pushed to production.

Instead of launching these resources manually, I used CloudFormation. When I need to delete the resources created by the template, I can simply delete the CloudFormation stack, and it will automatically delete all the resources within it.

Other resources created in this template include networking resources like VPCs, internet gateways, route tables, and subnets. They're also in the template because a production environment has specific requirements around traffic that it should enable and block out Setting up all of the networking resources that will help the deployment work is common practice.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-5)

## Deployment Scripts

Scripts are mini programs that help automate the running of commands. As part of setting up CodeDeploy, I wrote scripts to automate the deployment commands needed on the EC2 instance, so it can properly install, start, and host the web app

The 'install_dependencies' script helps my EC2 instance install all the dependencies it needs to host a web app, such as Tomcat

The start_server.sh script starts both Tomcat (our Java application server) and Apache (our web server) and makes sure they restart automatically if the EC2 instance ever reboots.

The stop_server.sh script safely stops the web server services by first checking whether they're running. It uses pgrep to detect active Apache (httpd) and Tomcat processes, and only attempts to stop a service if it's actually running.

## appspec.yml

Then, I wrote an appspec.yml file to give CodeDeploy instructions for deploying the web app. The key sections in appspec.yml are ApplicationStop (uses the 'stop_server.sh' script), BeforeInstall (uses the 'install_dependencies.sh' script to install dependencies like Tomcat), and ApplicationStart (uses the 'start_server.sh' script).

I also updated buildspec.yml to tell CodeBuild to package the new appspec.yml file and my deployment scripts alongside the compressed war file, all within the build artifact.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-12)

## Setting Up CodeDeploy

A deployment group is a set of EC2 instances that you can deploy to, along with the settings that determine how your web app should be deployed. A CodeDeploy application acts as a container that organizes all the deployment groups belonging to the same app.

To set up a deployment group, you also need to create an IAM role that gives CodeDeploy permission to access and coordinate with the EC2 instances involved in the deployment. Without this role, CodeDeploy has no way to identify or communicate with your instances, meaning it can't send them the instructions needed to carry out the deployment.

Tags are helpful for identifying which instances will be deploying the web app. I used the tag 'role:webserver' so my deployment group would automatically match the EC2 instance I deployed with my CloudFormation template. In the future, if I want other EC2 instances to join this same deployment group, I can simply apply the same 'role:webserver' tag to them, and they'll automatically be included which is a great timesaver.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-18)

## Deployment configurations

Another key setting is the deployment configuration, which affects how quickly and how risky the deployment is. I used CodeDeployDefault.AllAtOnce, so any changes that CodeDeploy deploys affect all the instances in the deployment group at once. This is the fastest way to deploy a change or code update, though it also carries the most risk since there's no gradual rollout to catch problems before every instance is affected.

To connect the deployment instance with CodeDeploy, a CodeDeploy Agent is installed on the instance. The agent's role is to receive deployment instructions from CodeDeploy and execute the commands defined in appspec.yml.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-20)

## Success!

Another key setting is the deployment configuration, which affects how fast and how risky the deployment is. I used CodeDeployDefault.AllAtOnce, so any change CodeDeploy deploys goes out to all instances in the deployment group at the same time. This is the fastest way to deploy a code update.

I had to configure a revision location, meaning where the web app's WAR file (the compressed file ready to be deployed) lives. My revision location is the S3 bucket I created, which is linked to CodeBuild, so build artifacts automatically land in that bucket.

To confirm the deployment was successful, I visited the public IPv4 DNS address of the EC2 instance running my deployment. I saw the live web app, confirming it was working and correctly serving the application's code to end users.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_val-27)

## Disaster Recovery

In a project extension, I decided to intentionally create a broken deployment. The purpose was to practice deployment recovery, a critical skill for scenarios where a failed deployment takes down your application. I caused the deployment to fail by introducing a wrong error into stop_server.sh.

I also enabled rollbacks for this deployment, which means if it fails, CodeDeploy will automatically redeploy the previous successful revision of the app.

When my deployment failed, the automatic rollback didn't happen on its own, because automatic rollback isn't enabled by default in CodeDeploy, you have to explicitly turn on 'roll back when a deployment fails' (or 'roll back when alarm thresholds are met') in the deployment group settings. To actually recover from the failure, I'd have to manually fix the underlying issue, like removing the conflicting file and then redeploy the last known-good revision myself. In production environments, this is exactly why automatic rollback should be configured upfront: it lets CodeDeploy detect a failed or unhealthy deployment and automatically redeploy the last stable version, rather than leaving the application broken until someone notices and steps in.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/836cda66-f725-5082-bdb3-0152b1d7a61b_rollback-validation-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/836cda66-f725-5082-bdb3-0152b1d7a61b)*
