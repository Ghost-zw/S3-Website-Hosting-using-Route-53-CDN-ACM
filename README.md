# S3-Website-Hosting-using-Route-53-CDN-ACM
S3 Website hosting using amazon Route 53, Cloudfront and ACM
This guide is going to show you how to create an Amazon S3 Website, using Amazon Route 53, Amazon Cloudfront, Amazon Certificate Manager

# Architecture 

<img width="3597" height="1551" alt="S3 website hosting" src="https://github.com/user-attachments/assets/4dc74f65-e154-44a3-9a48-d067c23eaffb" />

This diagram shows the key components of our setup, including:

Amazon S3 for hosting our Website
Route 53 a Scalable Domain Name System (DNS) web service.
Cloudfront for Content Delivery Network (CDN) that securely delivers data, videos, applications, and APIs to users with low latency.
Amazon Certifocate Manager a service that simplifies the process of provisioning, managing, and deploying SSL/TLS certificates for AWS services.

As we progress through this guide, we'll set up each of these components step by step.

## Table of Contents
1. [Overview of Hosting a Static S3 website](#overview)
2. [Why we need to  host a static S3 website ](#StaticS3Website)
  - Phase 1 : [Create S3 Bucket](#CreateS3Bucket)
  - Phase 2 : [Request a Certicficate with ACM](#RequestACertficate)
  - Phase 3 : [Create Cloudfront Distribution](#Cloudfront)
  - Phase 4 : [Setting Up Route 53](#Route53-Setup)
  - Phase 5 : [Test the the whole solution](#Testing)
3. [Conclusion](#Conclusion)

# Overview of Hosting a Static Website on S3 using Route 53, Cloudfront and ACM Architecture <a name="overview"></a>

Hosting a static website on AWS using S3, Route 53, CloudFront, and ACM involves a secure, scalable architecture. The static content (HTML, CSS, JS) is stored in an S3 bucket with static website hosting enabled. CloudFront acts as a global CDN, fetching content from S3 and delivering it with low latency, while Origin Access Control (OAC) ensures S3 objects are only accessible through CloudFront. AWS Certificate Manager (ACM) provides a free SSL/TLS certificate for HTTPS, which is attached to the CloudFront distribution. Route 53 manages DNS, routing your custom domain (e.g., `example.com`) to the CloudFront endpoint via an alias record. This setup ensures fast, secure, and reliable delivery of static content across the globe.

**Why we need to Host a Static Website on S3  ?** <a name="StaticS3Website"></a>

Hosting a static website on Amazon S3 offers a highly reliable, cost-effective, and scalable solution for serving simple web content like HTML, CSS, JavaScript, and images. It eliminates the need for managing servers, making it ideal for personal blogs, portfolios, landing pages, and documentation sites. S3 provides automatic high availability and durability, while integrating seamlessly with services like CloudFront for global content delivery and Route 53 for custom domain routing. With built-in support for static website hosting and granular access control, S3 makes it easy to launch secure, fast-loading websites with minimal infrastructure overhead.

## Phase 1: CREATE S3 Bucket
<a name="CreateS3Bucket"></a>

<p>1.Log in to the AWS Management Console.</p>
<p>2.Navigate to S3.</p>
<p>3.Create a Bucket:</p>
<p>4.Name your bucket (e.g., example.com).</p>
<p>5.Select a region.</p>
<p>6.Enable "Block all public access" and configure bucket policy to allow public read access for website files.</p>
<p>7.Upload Website Files: Upload your static website files (HTML, CSS, JS) to the bucket.</p>
<p>8.Enable Static Website Hosting:</p>
<p>9.Go to the bucket properties, enable static website hosting, and specify the index and error documents.</p>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**1. Create S3 Bucket:** 

<img width="1891" height="805" alt="s3 bucket" src="https://github.com/user-attachments/assets/6c525bfb-0f6b-460d-b54a-3ad8271ef88d" />

**2. Block all Public access**

<img width="1916" height="800" alt="s3 bucket1" src="https://github.com/user-attachments/assets/9e565fd4-b516-4b43-bcc7-a1c97a60cb62" />

**3. Upload Website files**
<img width="1902" height="801" alt="s3 bucket upload" src="https://github.com/user-attachments/assets/ac979a66-bfdc-4edc-80c1-f5faa09b51a7" />

**4. Enable S3 static website hosting**

<img width="1897" height="792" alt="enable web hosting" src="https://github.com/user-attachments/assets/0978ec51-4bde-483c-be0d-7fa2d8a6742f" />

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Phase 2: Request a Certicficate with ACM
<a name="RequestACertficate"></a>

<p>1.Navigate to AWS Certificate Manager.</p>
<p>2.Request a Certificate:</p>
<p>3.Choose "Request a public certificate."</p>
<p>4.Enter your domain name (e.g., example.com and www.example.com).</p>
<p>5.Validate ownership via DNS or email (DNS validation is recommended).</p>
<p>6.Complete Validation: Follow the instructions to validate your domain ownership.</p>

**1. Request Certificate.**

<img width="1906" height="466" alt="request cert" src="https://github.com/user-attachments/assets/66668b3c-44b0-4a3b-9ac4-73e21e984db7" />

**2. Go to Review and Request Certificate.**
<img width="1896" height="798" alt="request cert1" src="https://github.com/user-attachments/assets/27392f14-73a4-42db-a00a-e94cb66f9cac" />

**3. Create a record in Route 53.**
<img width="1906" height="798" alt="cert creation" src="https://github.com/user-attachments/assets/3bc95c34-0911-4d2b-ad56-0cd65f5bb520" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Phase 3: Create Cloudfront Distribution
<a name="Cloudfront"></a>

<p>1.Navigate to CloudFront.</p>
<p>2.Create a Distribution:</p>
<p>3.Choose "Web" distribution.</p>
<p>4.Set the origin to your S3 bucket (e.g., example.com.s3.amazonaws.com).</p>
<p>5.Enable "Redirect HTTP to HTTPS" for secure access.</p>
<p>6.Select the ACM certificate you created earlier for HTTPS.</p>
<p>7.Configure caching and other settings as needed.</p>
<p>8.Deploy the Distribution: Once created, note the CloudFront domain name (e.g., d1234567890abcdef.cloudfront.net).</p>

**1. Create Cloudfront Distribution.**
<img width="1912" height="803" alt="cloudfront" src="https://github.com/user-attachments/assets/051236b7-a664-46a5-916a-0b48d5e56852" />

**2. Specify Origin.**
<img width="1897" height="800" alt="cloudfront bucket" src="https://github.com/user-attachments/assets/1d5b5d51-26da-4dac-a181-8944a7998659" />

**3. Do not enbale security.**
<img width="1901" height="451" alt="cloudfront security" src="https://github.com/user-attachments/assets/b278d074-ade9-433a-8f46-79486bd43da3" />

**4. Get TLS Certificate.**
<img width="1892" height="653" alt="cdn ssl certificate" src="https://github.com/user-attachments/assets/70817dca-ad1e-4326-a260-d84f734786f4" />

**5. Review all configs and create.**
<img width="1897" height="797" alt="cdn review" src="https://github.com/user-attachments/assets/121814d1-4c1e-4046-8437-5dfa9b0a78c1" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Phase 4: Setting Up Route 53
<a name="Route53-Setup"></a>

<p>1.Navigate to Route 53.</p>
<p>2.Create a Hosted Zone:</p>
<p>3.If you haven’t registered your domain, do so in Route 53 or another registrar.</p>
<p>4.Set Up DNS Records:</p>
<p>5.Create an A record for your root domain (example.com).</p>
<p>6.Create an Alias record  pointing it to the CloudFront distribution.</p>
<p>7.Optionally, set up a redirect from www to the root domain using an S3 bucket configured for redirection.</p>

**1. Create an A record.**
<img width="1893" height="797" alt="route 53" src="https://github.com/user-attachments/assets/66c5a718-9631-4355-8170-b72c37d9739f" />

**2. Create an Alias record and point it to the Cloudfront distribution.**

<img width="1902" height="696" alt="route 53-1" src="https://github.com/user-attachments/assets/9d26cb22-1132-4ffa-ad43-573810117bb3" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Phase 5: Test the the whole solution
<a name="Testing"></a>

**1. Enter your web address linked to your domain eg example.com.**
l created a simple HTML file for testing this whole solution.

<img width="1908" height="960" alt="testing" src="https://github.com/user-attachments/assets/43fcfe67-1f69-43a2-9c18-f2d597ef88c4" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Conclusion 😁

By following these steps, you can effectively host a static website on Amazon S3, utilize CloudFront for faster content delivery, manage your domain with Route 53, and secure your site with ACM. This architecture is scalable, cost-effective, and provides a seamless experience for users accessing your website.
A blazing-fast website that loads in under 2 seconds globally, costs 94% less than traditional hosting, and scales automatically.

## Future improvements I'm implementing:

<p>✓ Automated deployment pipeline with GitHub Actions</p>
<p>✓ AWS WAF integration for security</p>
<p>✓ Multi-region failover setup</p>
<p>✓ Cost optimization with S3 Intelligent Tiering</p>











