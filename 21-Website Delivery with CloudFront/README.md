<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Website Delivery with CloudFront

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-cloudfront)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Website Delivery with CloudFront

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_1dddddwe)

---

## Introducing Today's Project!

In this project, I will demonstrate website delivery with cloudfront. I'm doing this project to learn why Content Delivery Networks (CDNs) exist with Amazon CloudFront.

### Tools and concepts

Services I used were S3 and CloudFront. Key concepts I learnt include content delivery network (CDN), Origin Access Controls(OAC), Distributions, S3 static website hosting vs CloudFront.

### Project reflection

This project took me approximately 2 hours. The most challenging part was understanding the Origin Access Controls (OAC). It was most rewarding to finally understand the OAC and its bucket policy, also to see the difference in Load time between the CloudFront and S3 hosting.

I chose to do this project today because i wanted to leran how content delivery works and develop more cloud engineering skills.

---

## Set Up S3 and Website Files

I started the project by creating an S3 bucket to hold the files that make up my website. I can't use CloudFront for this task because it is not a storage solution. Cloudfrint is a content delivery network that simply hosts content that is stored somewhere else, like Amazon S3.

The three files that make up my website are index.html, which is the main file for a website. It's where you organise the text, pictures, and everything that makes up your webpage, style.css, which is where you write down the visual appearance of your website's HTML elements. It controls everything from font sizes and colors to layout designs, helping you keep a consistent style across your website, and script.js, which is a file that adds interaction to your website. It's where you would write the instructions for making things on your website move or change when you click a button or submit a form.

I validated that my website files work by opening it in my browser and seeing the webpage.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_qgo7wcd3)

---

## Exploring Amazon CloudFront

Amazon CloudFront is a content delivery network, which means it speeds up the distribution of your static and dynamic web content, such as .html, .css, .js, and image files. Businesses and developers use CloudFront because content delivery is fast.

To use Amazon CloudFront, you set up distributions, which are a set of instructions that tells CloudFront how to deliver your content I set up a distribution for my S3 bucket. The origin is "nextwork-three-tier-precious09.s3.eu-west-2.amazonaws.com"

My CloudFront distribution's default root object is the index.html file. This means it is the file that CloudFront serves when the website is visited.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_qgo7wcdt)

---

## Handling Access Issues

When I tried visiting my distributed website, I ran into an access denied error because the S3 bucket was private. CloudFront needs permission to access files in my S3 bucket.

My distribution's origin access settings were already set to Origin Access Control (OAC). This caused the access denied error because access was only enabled in the cloudfront distribution, but it was not allowed in the S3 bucket policy. S3 buckets allow private access by default.

To resolve the error, I set up origin access control (OAC). OAC is is a special user for CloudFront that prevents this. An OAC lets you keep your S3 bucket and objects not publicly accessible, while still making sure they can be accessed through CloudFront..

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_egrhntyu)

---

## Updating S3 Permissions

Once I set up my OAC, I still needed to update my bucket policy because the S3 bucket's policy still needs to explicitly grant the OAC permission to the bucket's contents.

Creating an OAC automatically gives me a policy I could copy, which grants OAC access to the files in the S3 bucket.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_eg98ntyu)

---

## S3 vs CloudFront for Hosting

For my project extension, I'm comparing S3 vs CloudFront based on the hosted website's URLs and permissions. "I initially had an error with static website hosting because permissions were only granted to CloudFront's OAC, not for public access to the S3 bucket itself."

I tried resolving this by enabling public access on the S3 bucket, but the error persisted — turning off the block only removes the restriction on public requests, it doesn't actually grant permission to access the objects. I still ran into an error because I need a bucket policy to explicitly grant permissions.

I could finally see my S3 hosted website when i added a new policy statement to the Bucket policy. This worked because the JSON statetemt enable public access in S3 bucket permission policy.

Compared to the permission settings for my CloudFront distribution, using S3 meant having to leave my whole storage bucket wide open to the public internet. I preferred the CloudFront setup instead, since it keeps my S3 storage hidden and protects my files, letting only verified traffic through the CDN.

---

## S3 vs CloudFront Load Times

Load time means mean how quickly content on your website loads. The load times for the CloudFront site were faster than the S3 site because CloudFront's CDN caches content closer to users globally, while S3 static website hosting serves files directly from a single region.

A business would prefer CloudFront when faster delivery is essential, especially for users located far from yout S# bucket's region. S3 static website hosting might be sufficient when speed is not a priority, and when hosting from a single region.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-cloudfront_12verpuh)

---

---
