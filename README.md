🌐 Static Website Hosting using AWS S3 and CloudFront

📌 Project Overview

This project demonstrates how to host a static website using Amazon S3 and deliver it globally with high performance using Amazon CloudFront (CDN).

The website is publicly accessible via CloudFront and uses S3 as the origin for storing static files like HTML, CSS, and images.

---

🧱 Architecture

User → CloudFront (CDN) → S3 Bucket (Static Website Hosting)

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
- Enter a unique bucket name (e.g., "nagaraj-static-site")
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
  - "index.html"
  - "style.css"
  - "error.html"
- Click Upload

---

🔹 Step 5: Enable Static Website Hosting

- Go to Properties tab
- Scroll to Static Website Hosting
- Click Edit
- Enable hosting
- Set:
  - Index document: "index.html"
  - Error document: "error.html"
- Save changes

---

🔹 Step 6: Add Bucket Policy for Public Access

Replace "YOUR-BUCKET-NAME" with your actual bucket name and add the following policy:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadAccess",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}

---

🔹 Step 7: Create CloudFront Distribution

- Navigate to CloudFront
- Click Create Distribution

---

🔹 Step 8: Configure Origin

- In Origin Domain, select your S3 bucket
- Choose appropriate origin type:
  - S3 bucket OR
  - S3 static website endpoint
- Set Viewer Protocol Policy to:
  - Redirect HTTP to HTTPS

---

🔹 Step 9: Access Website via CloudFront

- Wait for distribution status = Deployed
- Copy CloudFront domain name
- Open in browser:

https://your-distribution-name.cloudfront.net

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

❌ Website Not Loading

- Verify "index.html" exists
- Check Default Root Object in CloudFront

❌ Delay in Website Availability

- Wait for CloudFront deployment (5–10 minutes)
