<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://nextwork.ai/projects/aws-host-a-website-on-s3)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use S3 to host a ststic website. I'm doing this project to learn about AWS and cloud services.

### Tools and concepts

Services I used were Amazon S3. Key concepts I learnt include bucket policies, uploading static website files, index.html. bucket endpoint url and ACLs and how it controls access to bucket objects.

### Time, challenges, and wins

This project took me approximately an hour. The most challenging part was resolving the 403 forbidden error. It was most rewarding to see the webpage load live and be public.

---

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I will create a bucket in Amazon S3, because this is where i will store the files that make up my website.

### How long it took to create the bucket

Creating an S3 bucket took me less than 5 minutes.

### Region selection

The Region I picked for my S3 bucket was London, because it is the region closest to me.

### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means no two S3 buckets can have the same name in the entire world regardless of region or the account.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step, I will upload the website files into the S3 bucket, because we need the files to create a website.

### Files I uploaded

I uploaded two files to my S3 bucket - they were an index.html file and which determines the structure and a folder of images and assets.

### How the files work together

Both files are necessary for this project as the index.html determines the structure but it does not illustrate the structure of the website, thats why i have multiple files uploded like assets and images for the html file to illustrate the website.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will make my website available for access, this is called static website hosting and it is important because the website files will stay as just files and not turn into website without this step.

### Understanding website hosting

Website hosting means putting our website files on a webserver which is a computer designed to turn the files into a website page.

### How I enabled website hosting

To enable website hosting with my S3 bucket, I went to the properties tab of my bucket and enabled static website hosting and also enabled index.html as my index document.

### Access Control Lists (ACLs)

An ACL is a way to configure permission settings inside a bucket. I enabled ACL so i can control access to my website files later.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is a URL that takes you and anyone on the internet to the website that you are hosting 

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I saw an error which was a 403 Forbidden error. The reason for this error was that objects in the bucket are public by default even after switching off the block all public access option but the website files are still completely private, they need to be make public files too.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I will go into the uploaded files and make them public because it will make the contents visible to anyone. once done the website is officially live.

### How I resolved the 403 error

To resolve this 403 Forbidden error, I selected the uploaded files, selected actions and made the files public using ACL. Basically i updated the access settings of the files inside the bucket.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension I'm about to use bucket policies to control access to my bucket files. I'm doing this so that i can stop people from deleting objects inside the file.

### Understanding bucket policies

An alternative to ACLs are bucket policies, which are... The benefit of using bucket policies which are rules that define who is allowed or not allowed to do someting, you can have greated control of the actions people and allowed and not allowed to do. while ACLs are useful for controlling public access to individual objects inside the bucket.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

My bucket policy denies everyone from deleting the index.html file. I tested this by trying to delete index.html and saw a permission denied error which means the bucket policy works.

---

---
