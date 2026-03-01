# AWS Demo Misconfiguration 1: S3 Public Bucket
Simulates a real-world AWS S3 security misconfiguration, where an S3 bucket is made public—exposing sensitive data to the internet.And it demonstrates both the vulnerability and the remediation.

# Scenario
An Amazon S3 bucket was deliberately misconfigured with public access enabled. Within this bucket, a file named secret.txt containing simulated sensitive credentials was uploaded. Because of the misconfiguration, the file became openly accessible to anyone on the internet without authentication.

This scenario illustrates one of the most common cloud security pitfalls: exposing internal data through overly permissive storage settings. Such mistakes often arise from developer oversight or misconfigured CI/CD pipelines, and have been repeatedly leveraged in real-world breaches to gain unauthorized access to confidential information.

# LAB Steps
## 1. Create S3 Bucket With Public Misconfiguration

From the start of being creat a bucket we have this screen
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/427745ac4a5e8045f5d6bfd829873d932a1db142/01_Start_to_creat_Bucket.png)

In setting of bucket we do not block all all public access
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/02_Bucket_public_settings.png)

## 2. Upload Sensitive File
Upload a Sensitive File on your device
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/03_Upload_file.png)

## 3. Apply Insecure Policy On Your Bucket
In your bucket, find 'Permissions' and bucket policy in there to edit this in:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::project-misconfig-demo/*"
    }
  ]
}
```
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/04_Bucket_policy_public.png)

## 4. Public Access File On Internet (No Have Login Request)
In your bucket, click to your file and copy your Object URL and search it. You will see if anyone else have your Object URL, they can see all your sensitive files.

![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/05_Everyone_access_browser.png)

# Remediation
## 5. Remove The Insecure Bucket Policy
Go back to Bucket Policy and delete it

![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/06_Bucket_policy_removed.png)

## 6. Validate Fix
Search that Object URl again to see the different
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/07_Get_access_denied.png)

## 7. Overview The Bucket In Lesson
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/5f611cc739813477eb6ba6612b48a7ddc4b5f503/08_Last_view_bucket.png)

# Learned Form Project
. Understanding Cloud Misconfigurations that we gained hands-on experience with how simple mistakes—like enabling public access on an S3 bucket—can expose sensitive data to the entire internet.
. Always enable "Block All Public Access" unless in some special siutiation
. Never upload sensitive data in publicly accessible buckets
. Have S3 Access Analyzer and IAM policies to hander secure permission management

# What I Got
. Practive like a security analyst with cloud misconfigurations
. Know how misconfiguration can expose data
. Real experience with AWS S3 configuration and the policy

# Project Files
```json
AWS-Demo-Misconfiguration-1:S3-Public-Bucket/
├── 01_Start_to_creat_Bucket.png
├── 02_Bucket_public_settings.png
├── 03_Upload_file.png
├── 04_Bucket_policy_public.png
├── 05_Everyone_access_browser.png
├── 06_Bucket_policy_removed.png
├── 07_Get_access_denied.png
├── 08_Last_view_bucket.png
├── README.md
└── secret.txt
```
# Author
ImSAM-S
