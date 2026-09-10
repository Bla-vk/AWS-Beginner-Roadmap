<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-kms)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate encryption of data with AWS KMS. The goal is to create encryption keys with AWS KMS (Key Management Service) and encrypt a DynamoDB database with a KMS key.

### Tools and concepts

Services I used include AWS Key Management Service(KMS), Amazon DynamoDB, AWS IAM management. Key concepts I learnt include encryption, decryption, kms key user management, DynamoDB Table's creation, assigning encryption key, and KMS keys lifecycle management.'

### Project reflection

This project took me approximately an hour. It was most rewarding to test IAM user policies. 

I chose to do this project today because i wanted to learn what AWS KMS is as it is part of the cloud engineering project track. 

---

## Encryption and KMS

Encryption is the process of using algorithms to convert data into a secure format called ciphertext, only authorised users can decrypt and restore the data to its original, readable state. Companies and developers do this to secure data, files, transactions and more. Encryption keys are what tells the algorithm exactly how it would transform plain text into the jumbled up format called cipher text for encryption.

AWS KMS is a secure vault for your encryption keys. Key management systems are important because they help manage all your encryption keys, what it can encrypt or who has access, in one place.

Encryption keys are broadly categorized as symmetric and asymmetric encryption. I set up a symmetric key because it is generally faster and more efficient for encrypting large amounts of data.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is a fully managed, serverless NoSQL database service provided by Amazon Web Services (AWS) that delivers single-digit millisecond performance at any scale.'

The different encryption options in DynamoDB include AWS owned key, AWS managed key and Customer managed key. Their differences are based on ownership, management and storage. I selected Customer managed key because, the key is stored in my IAM user account and can be managed by me(user).



![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by allowing encryption ad decryption of DynamoDB items by authorized users. 

Despite encrypting my DynamoDB table, I could still see the table's items because i have permission as an authorized user. DynamoDB uses transparent data encryption, which means your data is secure at rest, yet still accessible to authorized users that have the right permissions.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to test if a user without access to my KMS key can view the data in DynamoDB. The permission policies I granted this user are restricted to AmazonDynamoDBFullAccess but not to AWS KMS. 

After accessing the DynamoDB table as the test user, I encountered an error because i do not have permission to Kms:decrypt. This confirmed that the KMS key works by granting permission to authorized users only. 

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

To let my test user use the encryption key, I added the test user under the Key Users, which grants the right for kms:Encrypt", "kms:Decrypt", "kms:ReEncrypt*", "kms:GenerateDataKey*", and "kms:DescribeKey. My key's policy was updated to allow the test user to access the encrypted data. 

Using the test user, I retried to view the data in the DynamoDB table items. I observed that the table item is now visible, which confirmed that the test user now has the permissions to decrypt the data which was once encrypted by the IAM Admin user.

Encryption secures data instead of just securing the services/resources. I could combine encryption with access control to improve the overall security posture and create safeguarding rule, which should be used by individuals/organizations to prevent data breach.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-kms_feffb2fb8)

---

---
