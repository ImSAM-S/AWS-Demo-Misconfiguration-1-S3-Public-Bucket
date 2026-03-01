# AWS Demo Misconfiguration 1: S3 Public Bucket
Simulates a real-world AWS S3 security misconfiguration, where an S3 bucket is made public—exposing sensitive data to the internet.And it demonstrates both the vulnerability and the remediation.

# An Exemple in real life
An S3 bucket was configured with public access enabled. A sensitive file (secret.txt) containing fake credentials was uploaded. This file became accessible to anyone on the internet without authentication.

This simulates a common mistake made by developers or misconfigured CI/CD pipelines, and is frequently exploited in real-world breaches.

# LAB Steps
## 1. Create S3 Bucket with Public Misconfiguration

From the start of being creat a bucket we have this screen
![image alt](https://github.com/ImSAM-S/AWS-Demo-Misconfiguration-1-S3-Public-Bucket/blob/427745ac4a5e8045f5d6bfd829873d932a1db142/01_Start_to_creat_Bucket.png)
