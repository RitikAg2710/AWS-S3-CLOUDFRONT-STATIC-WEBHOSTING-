# AWS-S3-CLOUDFRONT-STATIC-WEBHOSTING-

# 📦 AWS S3 + CloudFront Static Website Hosting

This repository contains step-by-step instructions to host a static website using **Amazon S3** and deliver it securely using **CloudFront CDN** with HTTPS.

---

## 🌐 Live Demo

```bash
https://<your-cloudfront-distribution>.cloudfront.net/
```

---

## 🗂️ Folder Structure

```
project-root/
├── index.html
├── style.css
├── images/
│   └── bg.jpg
└── README.md
```

---

## ✅ Step-by-Step Guide

### 1. Create S3 Bucket
- Go to AWS → S3 → Create Bucket
- Bucket name: `s3-yourbucketname`
- Region: `ap-south-1` (or nearest)
- **Uncheck**: Block all public access ✅

### 2. Upload Website Files
- Upload `index.html`, images, css etc. to **bucket root**

### 3. Enable Static Website Hosting
- S3 → Bucket → Properties → Static Website Hosting
- Enable and set:
  - Index Document: `index.html`

### 4. Add Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::s3-yourbucketname/*"
    }
  ]
}
```

### 5. Create CloudFront Distribution
- Go to CloudFront → Create Distribution
- **Origin Domain**: `s3-yourbucketname.s3-website.ap-south-1.amazonaws.com`
- **Origin Protocol**: HTTP only
- **Viewer Protocol Policy**: Redirect HTTP to HTTPS
- **Default Root Object**: `index.html`

### 6. Invalidate Cache (After Updates)
- CloudFront → Your Distribution → Invalidations
- Path: `/*`

---

## 🎯 What You Get

- ✅ HTTPS-secured static website
- ✅ Global caching via CDN
- ✅ S3 as scalable, cost-efficient backend

---

## 🧠 Interview Tip

> “I hosted a static website on S3 and delivered it over HTTPS using CloudFront. I configured the custom origin with the S3 website endpoint and used bucket policy + cache invalidation for secure and optimized delivery.”

---

## ✍️ Author

**Ritik Agrawal**  
GitHub: [@RitikAg2710](https://github.com/RitikAg2710)

---

