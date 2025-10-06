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
2. [Why we need to  host a static S3 website ](#EC2StateChange)
  - Phase 1 : [Create SNS](#CreateSNSTopic)
  - Phase 2 : [Launch EC2 Instance](#LaunchEC2Instance )
  - Phase 3 : [Create Lambda Function](#Lambda)
  - Phase 4 : [Setting Up the Rules with Eventbridge](#Eventbridge-Setup)
  - Phase 5 : [Test the the whole solution and checking notifications](#Testing)
3. [Conclusion](#Conclusion)




