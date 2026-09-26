<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](https://nextwork.ai/projects/b71d29bd-8a1b-5fe0-9572-1c575423d558)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7a1de541)

## Introducing Today's Project!

In this project, I will demonstrate how to set up a web app in the cloud using AWS and VS Code. I'm doing this project to learn about CI/CD pipelines for DevOps.

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tomorrow. 

I did this project to kickstart the 6 days DevOps challenge. 

### Key tools and concepts

Services I used were AWS EC2 and VS Code. Key concepts I learned include establishing SSH connections, using an IDE to connect to an instance, editing an index.jsp file, and working with key pairs.

### Project reflection

This project took me approximately 3.5 hours. The most challenging part was using VS Code to remotely connect to the EC2 instance, which initially failed. I had to troubleshoot the error and later discovered it was an instance type problem. I changed the instance type from t3.micro to t3.small, which resolved it. The most rewarding part was finally being able to connect VS Code remotely to the server.

One thing I didn't expect in this project was how many concepts I'd need to apply, along with the amount of troubleshooting required. I also didn't expect using the local terminal to edit the index.jsp file, then seeing the changes reflected in the VS Code window. 

## Launching an EC2 instance

### What I did in this step

In this step, I will launch a new EC2 instance, set up a key pair for secure access and set up network settings for my instance.

I started this project by launching an EC2 instance because i want my web app to be entirely created and run on the cloud, i'll use a virtual server (EC2 instance) to house my development work.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7852fbf3)

### I also enabled SSH

SSH (Secure Shell) is basically a protocol that lets you securely connect to and control a remote server, using a password or key to prove it's really you. I enabled SSH so only my IP can connect over SSH.

### Key pairs

A key pair is like a lock and key for our EC2 instance used for authentication, so we can securely access it. It works using two mathematically linked keys: a public key on the instance, and a private key kept on my machine, which together prove my identity without the private key ever being transmitted.

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded a file called nextwork-keypair.pem. This file contains my private key which is the secret half of the key pair that only I hold that I'll need later in this project to securely access my EC2.

## Set up VS Code

### What I did in this step

In this step, I will set up a terminal in VS Code, so i can communicate with my EC2 instance and also update my key pair's permission settings, so i can use it to log into my EC2 instance later.

### What is VS Code?

VS Code is a lightweight source code editor (software for writing and editing code) that can function like a full IDE thanks to its massive library of extensions, making it compatible with a wide range of languages and use cases.

I installed VS Code to connect to my EC2 instance and then create and edit web app files on it.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_53d05e68)

## My first terminal commands

A terminal is where you send instructions to your computer using text instead of clicks. The first command I ran for this project was cd Desktop/DevOps, which changes my terminal's current working directory to the DevOps folder.

### Updating file permissions

I also updated my private key's permissions by running the command "chmod 400 nextwork-keypair.pem". This command stands for "change mode", and it changes the permissions of your .pem file. Using 400 makes it readable only by you (the owner) and restricts access for everyone else.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_9328ada1)

## SSH connection to EC2 instance

### What I did in this step

In this step, I will connect to my EC2 instance from my VScod terminal.

### Connecting to EC2

To connect to my EC2 instance, I ran the command ssh -i [PATH TO .PEM FILE] ec2-user@[IPv4 DNS of the EC2 INSTANCE]. This command established an SSH connection using my private key (the .pem file) and the instance's public address to authenticate and log in.

### This command required an IPv4 address

A server's Public IPv4 DNS is a hostname that resolves to its public IPv4 address. Computers and servers connected to the internet can use this DNS hostname to look up and connect to that server, since DNS translates the hostname into the actual IP address needed for routing.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_e3069dca)

## Maven & Java

### What I did in this step

In this step, I will install Apacha Maven and Amazon Corretto 8 (a version of java) on my EC2 instance.

### Why I'm using Maven

Apache Maven is a tool that helps developers build and organize Java software projects. It also functions as a package manager, meaning it automatically downloads any external pieces of code your project depends on in order to work.

Maven is required in this project because it handles dependency management, pulling in external libraries and tools our application needs, and it also manages the build process for packaging our own web app once it's been developed.

### Why I'm using Java

Java is a popular programming language used to build different types of applications, from mobile apps to large enterprise systems.

Java is required for this project because Maven, which I just downloaded, is a tool that needs Java to operate. Maven itself runs on the JVM, and it also relies on the JDK to compile and build the Java web app. So Java needs to be installed first before Maven can be used.

## Create the Application

### What I did in this step

In this step, I will run maven commands in my terminal to generate a java web app.

### Creating the Java web app

I generated a Java web app using the command "mvn archetype:generate" which is a command that sets up a basic web app (using Maven's archetype template).

### Installing Remote - SSH

I installed the Remote - SSH extension, which lets you connect securely to another computer via SSH over the internet. I installed it specifically to connect VS Code directly to my EC2 instance. This means I can now use VS Code as an IDE for the Java web app files stored on that EC2 instance, making editing the app much simpler and more efficient.

### SSH configuration details

The configuration details required to set up a remote SSH connection include the SSH host's name (i.e., the EC2 instance's public IPv4 DNS), the location of the private key on my local machine, and the username used to connect to the SSH host.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_2939cf01)

## Create the Application

### Exploring the project structure

Using VS Code's file explorer, I could see all the files and subfolders under nextwork-web-project which are all part of the web-app.

Two of the project folders Maven creates are src and webapp. src (specifically src/main/java) contains the web app's Java source code and the backend logic. whereas webapp (technically src/main/webapp, a subfolder of src/main) contains the front-end resources like JSPs, HTML, and static assets that define what the user actually sees.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_45f91fd7)

## Using Remote - SSH

### What I did in this step

In this step, I will connect VScode to my EC2 instance.

### Updating the web app

The index.jsp is a file used in Java web apps. It's similar to an HTML file because it contains markup to display web pages.

I edited index.jsp using VS Code, even though the file is stored on my EC2 instance. This was possible because I'd set up a Remote-SSH connection between VS Code and the instance, letting me work in it as if it were a local project.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_7a1de541)

## Using nano

### Additional improvements

In this secret mission, I will edit my index.jsp file using the terminal instead of the IDE.

### Terminal vs IDE

An alternative to using IDEs is the Terminal. To edit index.jsp, I ran the command nano index.jsp.

Compared to using an IDE, editing index.jsp in the terminal felt a little less intuitive, since navigation and edits rely entirely on the keyboard( basic terminal editor like nano). I'd lean toward using an IDE if I needed to work on multiple files on the server at once

### Verifying my work

To verify my changes, I switched back to the VS Code window connected to my EC2 instance via Remote-SSH. Because that window and the terminal share the same SSH connection to the instance, my edits appeared immediately without needing to reconnect.. 

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/b71d29bd-8a1b-5fe0-9572-1c575423d558_a3324ad41)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/b71d29bd-8a1b-5fe0-9572-1c575423d558)*
