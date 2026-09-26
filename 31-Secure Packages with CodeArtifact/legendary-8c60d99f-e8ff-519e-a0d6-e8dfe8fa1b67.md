<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Packages with CodeArtifact

**Project Link:** [View Project](https://nextwork.ai/projects/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_1d79e699)

## Introducing Today's Project!

In this project, I demonstrate how to set up and use AWS CodeArtifact to manage and secure Java dependencies for my applications. My goal is to understand why an artifact repository is a critical part of a CI/CD pipeline.

### Key tools and concepts

The services I used included AWS CodeArtifact, IAM, Amazon EC2, GitHub, and VS Code. Key concepts I learned included working with artifact repositories, connecting Maven to CodeArtifact, and configuring IAM permissions to allow my EC2 instance to access CodeArtifact.

### Project reflection

This project took about two hours in total, including documentation, troubleshooting, and a secret mission. The most challenging part was working through CLI commands and resolving permission errors, while the most rewarding moment was watching CodeArtifact fill up with packages once the connection was finally set up correctly.

This project is part three of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

## CodeArtifact Repository

CodeArtifact is a secure, central place to store all your software packages. Engineering teams use artifact repositories because i'ts a reliable place to store and retrieve these components. This gives you three big benefits: which are security, reliability and control.

A domain is like a folder that groups multiple repositories together under the same project or organization. It lets you apply permissions and policies across multiple CodeArtifact repositories at once. My domain is called nextwork.

A CodeArtifact repository can have an upstream repository which means a public source of packages that Maven can pull from when a package isn't found in the local CodeArtifact repository. My repository's upstream is the Maven Central Repository, the largest Java package repository, which is extremely helpful when building a Java web app.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_n4o5p6q7)

## CodeArtifact Security

### Issue

To access CodeArtifact, I needed an authentication token granting my EC2 instance access for 12 hours. Retrieving the token initially failed because the instance had no permission to access AWS resources by default, a deliberate consequence of AWS's principle of least privilege, which requires permissions to be explicitly granted rather than assumed.

### Resolution

To resolve the security token error, I created an IAM policy granting access to CodeArtifact, then created an IAM role with that policy and attached it to my EC2 instance. This resolved the issue because my EC2 instance can now request an authorization token from my repository.

Using IAM roles is a security best practice because they provide temporary, automatically rotated credentials, which reduces the risk of exposed long-term access keys. They also enable secure cross-service and cross-account access without hardcoding credentials, improving overall security and compliance. As with any IAM identity, roles should still be scoped to the principle of least privilege by attaching only the permissions actually needed.

## The JSON policy attached to my role

The JSON policy grants the permissions needed to authenticate with and pull packages from AWS CodeArtifact. It allows codeartifact:GetAuthorizationToken, codeartifact:GetRepositoryEndpoint, and codeartifact:ReadFromRepository to access repository resources, along with sts:GetServiceBearerToken, scoped by a condition to CodeArtifact to securely generate the authentication token via AWS STS. Together, these permissions let developers and CI/CD pipelines pull dependencies without manual credential management.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_23rp7q8r9)

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures Maven's connection to AWS CodeArtifact by defining the repository URL and server authentication settings. It references a temporary authorization token generated separately using your AWS credentials, which lets Maven securely authenticate and download dependencies from CodeArtifact.

Compiling converts source code into a machine-readable format. I use Maven to manage my build process, and as part of that, it invokes a compiler to compile my code. Maven also handles dependency resolution, it checks CodeArtifact first for the packages my code needs, and if they aren't there, it fetches them from the upstream repository (Maven Central) and caches a copy in CodeArtifact for future use.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_c17eace8)

## Verify Connection

After compiling my web app, I checked my CodeArtifact repository and found 3 pages of packages listed. This confirmed that my dependencies had been successfully stored in the artifact repository."

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_1d79e699)

## Uploading My Own Packages

As an extension to this project, I also took on the role of package publisher, publishing my own packages to a CodeArtifact repository. This mirrors a real world scenario where internal team members build their own packages and need to share them with teammates without exposing them to the public.

To create my own package, I set up a text file and used tar to package it up. I also generated a security hash, which gives CodeArtifact a way to verify whether the package was tampered with in transit, if it was, the hash CodeArtifact generates from the received file won't match the hash I originally generated.

To publish the package, I run a CLI command to upload the package I created in CloudShell to my repository. Looking at the package details in CodeArtifact, I can see the version number, publish date, and origin since I published it directly rather than pulling it from an external source, the origin shows as 'Internal'.

To validate my package, I downloaded it from CodeArtifact using CloudShell, and it installed successfully. After unzipping the package, I found the text file I had created earlier, confirming that CodeArtifact correctly stored and returned my custom package.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67_sm12-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/8c60d99f-e8ff-519e-a0d6-e8dfe8fa1b67)*
