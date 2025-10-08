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
  - Phase 5 : [Test the the whole solution and checking notifications](#Testing)
3. [Conclusion](#Conclusion)

# Overview of Hosting a Static Website on S3 using Route 53, Cloudfront and ACM Architecture <a name="overview"></a>

Hosting a static website on AWS using S3, Route 53, CloudFront, and ACM involves a secure, scalable architecture. The static content (HTML, CSS, JS) is stored in an S3 bucket with static website hosting enabled. CloudFront acts as a global CDN, fetching content from S3 and delivering it with low latency, while Origin Access Control (OAC) ensures S3 objects are only accessible through CloudFront. AWS Certificate Manager (ACM) provides a free SSL/TLS certificate for HTTPS, which is attached to the CloudFront distribution. Route 53 manages DNS, routing your custom domain (e.g., `example.com`) to the CloudFront endpoint via an alias record. This setup ensures fast, secure, and reliable delivery of static content across the globe.

**Why we need to Host a Static Website on S3  ?** <a name="StaticS3Website"></a>

Hosting a static website on Amazon S3 offers a highly reliable, cost-effective, and scalable solution for serving simple web content like HTML, CSS, JavaScript, and images. It eliminates the need for managing servers, making it ideal for personal blogs, portfolios, landing pages, and documentation sites. S3 provides automatic high availability and durability, while integrating seamlessly with services like CloudFront for global content delivery and Route 53 for custom domain routing. With built-in support for static website hosting and granular access control, S3 makes it easy to launch secure, fast-loading websites with minimal infrastructure overhead.

## Phase 1: CREATE S3 Bucket
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


