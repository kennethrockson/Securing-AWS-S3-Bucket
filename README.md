# Securing-AWS-S3-Bucket

# Securing Data at Rest in AWS S3 Buckets

## Introduction
Welcome to my project on **Securing Data in AWS S3 Buckets**!  
AWS S3 is like a digital storage locker where you can keep files and data. This guide walks you through creating a secure S3 bucket, locking down access, enabling backup features, and more.

---

---

### Create an S3 Bucket
An S3 bucket is like a folder where you store your data in AWS.

#### Steps:
1. Log in to the **AWS Management Console**.
2. Navigate to the **S3 Dashboard**.
3. Click **Create bucket**.
4. Fill in the settings:

![Screenshot 2024-11-19 150206](https://github.com/user-attachments/assets/a7c93540-be2c-4aef-8061-15c38de94405)

During this I created my own custom KMS with the priority of security but also efficiency
![Screenshot 2024-11-19 153853](https://github.com/user-attachments/assets/53996fbe-2241-434b-bb10-00b6b1b578f5)

#### What it Does:
Creates a safe folder to store your data with public access blocked, ensuring privacy.

---

### Enable Bucket Versioning
Versioning keeps backups of your files, letting you restore older versions if needed.

#### Steps:
1. Go to the **S3 Dashboard**.

![Screenshot 2024-11-19 150659](https://github.com/user-attachments/assets/64938845-2143-401b-94bc-953698d38386)



#### What it Does:
Maintains copies of every version of your files, providing a safety net for recovery.

---

### Exercise 3: Enable Server-Side Encryption
Encryption locks your files with a special key, ensuring only authorized users can read them.

#### Steps:
1. Open the **S3 Dashboard** and select your bucket.
2. Go to the **Properties** tab.
3. Locate **Default encryption** and click **Edit**.
4. Turn on encryption with **AWS-KMS**:
   - Choose a key or let AWS create one.
5. Save changes.

#### What it Does:
Encrypts your files, making them unreadable to unauthorized users.

---

### Set Bucket Policies
Bucket policies define who can access your files and what actions they can take.

#### Steps:
1. Navigate to your bucket in the **S3 Dashboard**.
2. Open the **Permissions** tab.
3. Locate **Bucket Policy** and click **Edit**.
4. Add a rule like this (replace placeholders):
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
           "AWS": "arn:aws:iam::123456789012:user/username"
         },
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::my-secure-bucket/*"
       }
     ]
   }

Save changes.

What it Does:
Defines a rule allowing specific users access while keeping others out.


![Screenshot 2024-11-19 152934](https://github.com/user-attachments/assets/e21579dc-5a93-4c3b-b3fb-033e4be7655d)

Configure S3 Access Logs
Access logs record who accesses your files and when.

Steps:
Select your bucket in the S3 Dashboard.
Enable logging and select a separate bucket to store logs.
Save changes.

![Screenshot 2024-11-19 153217](https://github.com/user-attachments/assets/76b6f251-3023-46f6-a95b-8288664de1d8)


What it Does:
Tracks all access to your files, helping to monitor and detect suspicious activity.

Conclusion
By following these steps, I’ve secured an S3 bucket by:

Creating the bucket and blocking public access.
Enabling file versioning.
Locking files with encryption.
Setting specific access rules with bucket policies.
Enabling access logs for monitoring.

These steps are foundational for keeping your AWS S3 data safe. I hope this guide helps you secure your own storage with confidence!


