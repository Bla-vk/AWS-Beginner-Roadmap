<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Continuous Integration with CodeBuild

**Project Link:** [View Project](https://nextwork.ai/projects/92664c9b-5395-50c5-82bc-e72e574a6140)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_35588a47)

## Introducing Today's Project!

In this project, I will demonstrate how to use CodeBuild to automate and build processes in CI/CD pipeline. I'm doing this project to learn about the process of turning code into a package that can be deployed.

### Key tools and concepts

The services and tools I used include AWS CodeBuild, CodeConnections, CodeArtifact, EC2, and S3, alongside GitHub and VS Code. Key concepts I learned included the CI/CD build process, resolving Git issues from the terminal, writing buildspec.yml and run-tests.sh files, and using CodeConnections to link AWS with GitHub.

### Project reflection

This project took approximately 3 hours, including troubleshooting and documentation. The most challenging part was setting up CodeBuild. The most rewarding moment was watching the build succeed at the end.

This project is part four of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow.

## Setting up a CodeBuild Project

CodeBuild is a continuous integration (CI) service. It compiles code (turns a web app's code into something a computer can run), runs automated tests against it, and packages the result into a neat little bundle ready to deploy. Engineering teams use it because CI services automate this whole pipeline. Without CI, engineers would have to compile, test, and package code manually before every deployment which is slower and far more prone to human error.

My CodeBuild project's source configuration specifies where the code lives, and I selected GitHub, since that's where my web app's source code repository is.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_fewgrhte)

## Connecting CodeBuild with GitHub

GitHub offers several credential types for connecting to external services, including GitHub Apps, Personal Access Tokens, and OAuth Apps. I chose a GitHub App because it's the simplest and most secure way to connect GitHub to AWS. AWS manages the credentials in the background, so I only need to sign in once to authorize the AWS-managed GitHub App.

To connect my AWS environment with GitHub, I used AWS CodeConnections, a service that establishes secure connections between AWS and third-party platforms like GitHub. In my case, it authorized a secure link to my GitHub repository, allowing my CodeBuild project to use it as a source with the correct permissions.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_a7c98e2d)

## CodeBuild Configurations

### Environment

My CodeBuild project's Environment configuration defines the compute environment that runs the build, the underlying infrastructure that compiles and packages the files when the project runs. It includes settings like provisioning model, operating system, image, and service role. These settings determine how the build environment is provisioned and how the build process is carried out. It's important that this environment has the correct permissions (via its service role) to access everything it needs.

### Artifacts

Build artifacts are the files or resources produced during the CodeBuild build process. They matter because later stages of the CI/CD pipeline depend on them. For example, my build process generates a compressed file containing my web app, which I'll later use to deploy it. To store these build artifacts, I created an S3 bucket configured as the artifact location.

### Packaging

When setting up CodeBuild, I also chose to package artifacts into a zip file. This helps with package management, as all the files are organized neatly into a single archive. It also helps compress the size of the compiled web app.

### Monitoring

For monitoring, I enabled CloudWatch Logs, which collects and stores log data from my instance, including system events and application errors, so I can track activity and troubleshoot issues more easily

## buildspec.yml

My first build failed because CodeBuild couldn't find a buildspec.yml file in the root of my source directory. This file is required because it defines the commands CodeBuild runs at each build phase (install, pre-build, build, and post-build).

My buildspec.yml has four phases: the first two install Java and grant access to CodeArtifact, the third compiles the web app, and the fourth packages it into a single compressed artifact.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_35588a47)

## Success!

My second build also failed, but with a different error, this time it failed while executing the command to compile the web app, mvn -s settings.xml compile. To fix this, I need to add a new policy to CodeBuild that grants CodeArtifact permissions.

To resolve the second error, I attached a policy granting CodeArtifact access to my CodeBuild service role. Rebuilding the project returned a 'Succeeded' status, confirming that CodeBuild could now reach the repository with the necessary permissions.

To verify the build succeeded, I checked the artifact bucket in S3. The presence of the artifact confirmed that CodeBuild had completed successfully in pulling the source code from the GitHub repository, building it, packaging the output into a compressed file, and uploading that file to the S3 bucket.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_d9cc6191)

## Automating Testing

In a project extension, I created a simple unit test for my Java web application and triggered a build to confirm the tests run automatically. I added a test script that checks whether a src folder and an index.jsp file exist in my project directory.

To add the test script to the build process, I pushed the updated files (buildspec.yml and run-tests.sh) to my GitHub repository, then started a new build in CodeBuild that included the testing phase.

After pushing my code to GitHub, I triggered a build in CodeBuild, which pulled the updated code from GitHub and packaged my project according to the steps defined in buildspec.yml. I could see the test phase markers in the build logs.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/92664c9b-5395-50c5-82bc-e72e574a6140_sm-test-script-upload)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/92664c9b-5395-50c5-82bc-e72e574a6140)*
