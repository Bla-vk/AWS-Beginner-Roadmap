<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](https://nextwork.ai/projects/10d3e52a-a2ad-597e-9e1c-33526bde77ba)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_9i0j1k2l)

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to create an S3 bucket. The goal is to install and set up Terraform, troubleshoot any errors along the way (e.g., issues installing the CLI), and then successfully apply my Terraform configuration to provision the bucket.

### Tools and concepts

The tools and services I used were Amazon S3, AWS IAM, Terraform, and the AWS CLI. Key concepts I learned include infrastructure as code (defining infrastructure in configuration files), provider plugins that let Terraform communicate with AWS, state files that track the resources Terraform manages, and the dependency lock file, which pins provider versions.

### Project reflection

This project took me approximately one hour. The most rewarding part was seeing a local image I uploaded appear in my S3 bucket.

I chose to do this project today as an introduction to Terraform, because Infrastructure as Code is an essential skill in cloud environments.

## Introducing Terraform

Terraform is an infrastructure-as-code tool that lets you build and manage your cloud infrastructure using code. Instead of creating resources manually in the AWS console or CLI, you write configuration files that describe exactly what you want, such as servers, databases, and networks. Terraform then reads those files and builds the infrastructure for you, using your configuration as a blueprint.

Terraform is one of the most popular tools used for infrastructure as code (IaC), which is the practice of describing your cloud setup (like your servers, storage, networks) in plain text files instead of clicking through a web console. When you run those files, the cloud builds everything exactly as you've written it written.

Terraform uses configuration files to define and manage infrastructure. These files describe the desired state of your infrastructure, and Terraform works out the steps needed to reach that state. In most Terraform projects, main.tf is the primary configuration file. It's where you declare the resources you want, such as EC2 instances or S3 buckets, using HashiCorp Configuration Language (HCL). Think of it as the blueprint for building your cloud resources.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_9i0j1k2l)

## Configuration files

Terraform configurations are written as separate blocks (such as provider, resource, and variable blocks) rather than one continuous script. This makes it easier to update one part of main.tf, like a single resource, without rewriting the rest of the file. It also helps teams collaborate, since changes are smaller and easier to review.

### My main.tf configuration has three blocks

The first block shows that I'm using AWS as the provider for this infrastructure. The second block provisions an Amazon S3 bucket and gives it a unique name. The third block manages the bucket's public access settings, which blocks all public access to it.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_ljvh9876)

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to find ways to customize my bucket's configuration. The documentation provides example configurations, a list of all the available arguments for a resource, and rules for how each one is used.

I chose to customise my bucket by adding tags, because they let me identify which project the bucket belongs to. After I launch the bucket, I can verify the customisation by opening the bucket in the S3 console and checking the Tags section under the Properties tab.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_ffe757cd3)

## Terraform commands

I ran 'terraform init' to initialize my Terraform working directory. This configures the backend where Terraform stores its state file and downloads the required provider plugins, i.e., the AWS provider.

Next, I ran 'terraform plan' so Terraform would compare the resources defined in my main.tf file against the current state of my infrastructure and show me what changes it would make.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_3g4h5i6j)

## AWS CLI and Access Keys

When I ran terraform plan, I did not receive an error because my local terminal was already configured with AWS credentials, which the Terraform AWS provider picked up automatically.

I used the AWS CLI (Command Line Interface), which is a tool for interacting with my AWS infrastructure from the terminal. Instead of using the AWS Management Console, the CLI lets me run text commands to do the same things from my local computer.

I configured the AWS CLI on my local computer to access my AWS account using access keys. Once the Access Key ID and Secret Access Key are entered through aws configure, they are saved locally, so the CLI (and any tool using the AWS SDK) on this machine can authenticate to my AWS account.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_7j8k9l0m)

## Lanching the S3 Bucket

I ran terraform apply to apply the changes I wrote in my Terraform configuration. This command affects my AWS account by creating, modifying, or deleting resources so that my real infrastructure matches my code. In this case, it creates the S3 bucket in my AWS account.

The sequence of running terraform init, plan, and apply is crucial because each step depends on the one before it. terraform init prepares your project by downloading the required provider plugins and modules and configuring the backend where the state file will be stored. The state file is what Terraform uses to track the current state of your infrastructure. terraform plan then previews the changes Terraform would make, and terraform apply carries them out.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_1q2w3e4r)

## Uploading an S3 Object

I created a new resource block to upload an image called image.png to the S3 bucket. Because the object key is just image.png with no prefix, the image is stored at the root of the bucket instead of inside a subfolder.

We need to run terraform apply again because we've updated our Terraform configuration file, which means there are changes Terraform needs to review and compare against our current infrastructure. This time, only one new resource is created: the image.

To validate that my configuration was updated successfully, I checked the S3 bucket and confirmed that a new image had been added. I then downloaded the image back to my local machine and confirmed it matched the image I originally uploaded.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/10d3e52a-a2ad-597e-9e1c-33526bde77ba_9o0p1a2s)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/10d3e52a-a2ad-597e-9e1c-33526bde77ba)*
