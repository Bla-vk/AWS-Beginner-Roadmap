<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect a Web App with Aurora

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-webapp)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Connect a Web App to Amazon Aurora

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-webapp_1709b26b)

---

## Introducing Today's Project!

### What is Amazon Aurora?

Amazon Aurora is a fully managed, enterprise-grade relational database service built for the cloud by AWS that is fully compatible with MySQL and PostgreSQL. AWS manages time-consuming database tasks like OS/engine patching, hardware provisioning, and automated backups. It also has Multi-AZ deployments that synchronously replicate data to a secondary zone, providing automatic failover if the primary database fails.

### How I used Amazon Aurora in this project

I used Amazon Aurora to create and connect a managed MySQL database to my EC2 hosted web app for real-time data interaction.

### One thing I didn't expect in this project was...

How seamlessly I could manage and update database connections directly through the terminal using PHP.

### This project took me...

The project took me an Hour to complete.

---

## Creating a Web App

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-webapp_b7999168)

To connect to my EC2 instance, I moved my .pem file into a folder called NextWork on my Desktop, opened my terminal, navigated to that folder, set the file's permissions using chmod 400, and used the ssh -i command with the EC2 public DNS.

To help me create my web app, I first updated all the software on my EC2 instance using sudo dnf update -y. Then I installed Apache (httpd), PHP, the php-mysqli library, and mariadb105 for communication between my web server and db.

---

## Connecting my Web App to Aurora

I set up my EC2 instance's connection details to my database by creating a dbinfo.inc file in /var/www/INC. Then i added my Aurora endpoint, username, password, and database name using PHP define() statements.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-webapp_1709b25b)

---

## My Web App Upgrade

Next, I upgraded my web app by creating a SamplePage.php file in /var/www/html containing a PHP script that links to my Aurora database, enabling direct entry and retrieval of employee data.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-webapp_2709b25b)

---

## Testing my Web App

To make sure my web app was working correctly, I submitted sample data through the UI and confirmed its storage in the EMPLOYEES table by running SQL queries via the MySQL CLI.



![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-webapp_1409z22b)

---

---
