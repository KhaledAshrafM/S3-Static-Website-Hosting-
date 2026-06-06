[README(2).md](https://github.com/user-attachments/files/28665910/README.2.md)<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Khaled Ashraf  
**Email:** khaledashrafzzz583@gmail.com

---

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

### Project overview

In this project we are going to host a static website using the AWS storage service S3

### Tools and concepts

S3 Buckets and Objects — data in S3 is stored as objects inside buckets, and we learned how to upload files and organize them inside a bucket.
Public Access and Bucket Policies — we configured the bucket to allow public read access via bucket policy (s3:GetObject) so anyone can load the website.
AWS Region Selection — we chose eu-central-1 (Frankfurt) based on three factors: proximity to our users (Egypt), service availability, and pricing.

### Time, challenges, and wins

This project took me approximately half an hour to complete. 

---

## How I Set Up an S3 Bucket

### What I did in this step

First of all open the AWS console managanet then search for S3 and click on it.

### How long it took to create the bucket

### Region selection

As a general rule, when we consider choosing an AWS region we think about three things: 
- How close this region to your end users? to avoid high latency.
- What services are available?
- How are you going to be charged in this region.

For this project I chose Frankfort in Europe as it is the closest one to Egypt, where I live.

### Understanding bucket name uniqueness

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step we are going to upload in our S3 bucket the HTML file that sets up the website, also we will upload a zip file includes a collection of images.

### Files I uploaded

I uploaded two files to my S3 bucket - they were index.html (i.e. this file is responsible of determining the structure of the website) and a folder contains a collection of images and assets so we have something to display in our website.

### How the files work together

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, we are going to enable the static website hosting (i.e. making our website public over the internet).


### Understanding website hosting

Website hosting is simply the idea of having your HTML file stored on a web server so everyone can access it online.

### How I enabled website hosting

To enable website hosting with my S3 bucket, we went to "properties" tab and clicked "enable S3 static website hosting".

### Access Control Lists (ACLs)

An ACL is a set of roles controls which access is allowed and which is denied.
In this project I enabled it to have a micro-control over objects within the bucket.

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is the link that users can use in order to access our website, think of it as any link you daily use to access websites (the CNN URL for example).

### What I saw when I tested the endpoint

When We first visited the bucket endpoint URL, We faced the error "403 Forbidden" indicating that the access is denied. 

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, We will make our website files publicly accessible via updating the permissions of our files using ACLs. 
We selected the intended objects then using the "Actions" tab we chose "Make public using ACL". And now once we checked our bucket website endpoint could successfully reach the website and have our content displayed. 

### How I resolved the 403 error

To resolve this 403 Forbidden error, we have changed the permissions of our objects inside the bucket by allowing the public access to them using ACLs. 

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension we are about to configure bucket policies so no one can delete index.html file.

### Understanding bucket policies

Why using Bucket Policies? bucket policies are great when it comes to specify what actions can be done to individual objects within the bucket, unlike ACLs which only can permit or deny the public access to individual object, BP gives you a way to say what specific action can anyone do to the specific object.

![Image](http://learn.nextwork.org/cheerful_beige_innocent_camel/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

Specifically it explicitly denies s3:DeleteObject on index.html for everyone (*) — meaning nobody, including account users, can delete that file. It's a protection policy to prevent accidental or unauthorized deletion of the website's main file.

---

---

