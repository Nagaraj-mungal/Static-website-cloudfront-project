🌐 Static Website Hosting using AWS S3 and CloudFront

📌 Project Overview

This project demonstrates how to host a static website using Amazon S3 and deliver it globally with high performance using Amazon CloudFront (CDN).

The website is publicly accessible via CloudFront and uses S3 as the origin for storing static files like HTML, CSS, and images.

---

🧱 Architecture

User → CloudFront (cloudfront-nagaraj-static-site-123) → S3 Bucket (nagaraj-static-site-123)

---

⚙️ AWS Services Used

- Amazon S3 (Simple Storage Service)
- Amazon CloudFront (Content Delivery Network)
- AWS IAM (Identity and Access Management)

---

🚀 Step-by-Step Implementation

🔹 Step 1: Login to AWS Console

Login to the AWS Management Console using your credentials.

---

🔹 Step 2: Create S3 Bucket

- Navigate to S3
- Click Create bucket
- Enter bucket name: nagaraj-static-site-123
- Select region (e.g., ap-south-1)
- Click Create bucket

---

🔹 Step 3: Disable Block Public Access

- Open the created bucket
- Go to Permissions tab
- Click Edit under Block Public Access
- Uncheck Block all public access
- Save changes

---

🔹 Step 4: Upload Website Files

- Go to Objects tab
- Click Upload
- Upload:
  - index.html
  - style.css
  - error.html
- Click Upload

---

🔹 Step 5: Enable Static Website Hosting

- Go to Properties tab
- Scroll to Static Website Hosting
- Click Edit
- Enable hosting
- Set:
  - Index document: index.html
  - Error document: error.html
- Save changes

---

🔹 Step 6: Add Bucket Policy for Public Access

Replace with your bucket name:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::nagaraj-static-site-123/*"
    }
  ]
}

---

🔹 Step 7: Create CloudFront Distribution

- Navigate to CloudFront
- Click Create Distribution
- Distribution name: cloudfront-nagaraj-static-site-123

---

🔹 Step 8: Configure Origin

- In Origin Domain, select:
  
  - nagaraj-static-site-123.s3.amazonaws.com
    OR
  - S3 static website endpoint (if using website hosting)

- Set Viewer Protocol Policy to:
  
  - Redirect HTTP to HTTPS

- (Optional but recommended)
  
  - Set Default Root Object: index.html

---

🔹 Step 9: Access Website via CloudFront

- Wait for distribution status = Deployed
- Copy CloudFront domain name
- Open in browser:

https://cloudfront-nagaraj-static-site-123.cloudfront.net

---

🔐 Key Concepts

- Amazon S3 is used to store static website files
- CloudFront improves performance using caching and global edge locations
- Bucket policy enables public read access to files
- HTTPS ensures secure communication

---

⚠️ Common Issues & Fixes

❌ 403 Forbidden

- Check bucket policy
- Ensure public access is enabled

---

❌ Website Not Loading

- Verify index.html exists
- Check Default Root Object in CloudFront

---

❌ Delay in Website Availability

- Wait for CloudFront deployment (5–10 minutes)

---
