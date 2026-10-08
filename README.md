# 🌐 Static Website Deployment on AWS EC2

## 📌 Project Overview

This project demonstrates how I deployed a static website on an **AWS EC2 instance** using **Ubuntu Linux and Apache2**.

The website source code was stored in a GitHub repository, cloned onto the EC2 server, and then configured to be served publicly through the Apache web server.

This project helped me understand the basics of **cloud computing, Linux server management, Git/GitHub, web servers, networking, and website deployment**.

---

## 🚀 Live Website

The website was deployed on an AWS EC2 instance and accessed through its public IPv4 address.

**Deployment URL:**

`http://54.145.213.217`

> Note: The IP address may change if the EC2 instance is stopped and started unless an Elastic IP is configured.

---

## 🛠️ Technologies Used

- ☁️ **AWS EC2**
- 🐧 **Ubuntu Linux**
- 🌐 **Apache2 Web Server**
- 🔧 **Git & GitHub**
- HTML5
- CSS3
- JavaScript
- Linux Terminal
- UFW Firewall

---

## 🏗️ Deployment Architecture

```text
                 🌍 Internet
                     │
                     ▼
            Public IPv4 Address
               54.145.213.217
                     │
                     ▼
              ☁️ AWS EC2 Instance
                 Ubuntu Linux
                     │
                     ▼
                Apache2 Server
                     │
                     ▼
               /var/www/html
                     │
            ┌────────┼────────┐
            ▼        ▼        ▼
        index.html style.css script.js
            │
            ▼
       🌐 Live Website
---

## 📋 Deployment Steps

1. Launch an EC2 Instance

I created an EC2 instance on AWS with:

Instance type: t2.micro
Operating System: Ubuntu
Region: us-east-1
Public IPv4 address assigned by AWS

The EC2 instance acts as the cloud server for hosting the website.

2. Connect to the EC2 Instance

After launching the instance, I connected to it using SSH and accessed the Ubuntu terminal.

ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
3. Clone the GitHub Repository

I used Git to download the website source code onto the EC2 server.

git clone https://github.com/ShreyaBalpande/AWS_ec2.git

The repository contains the main website files:

index.html
style.css
script.js
4. Install Apache2

Apache2 was installed as the web server.

sudo apt update
sudo apt install apache2 -y

Apache is responsible for serving the website files to visitors over HTTP.

5. Copy Website Files to Apache's Web Directory

Apache's default web directory on Ubuntu is:

/var/www/html

I copied my website files into this directory:

sudo cp index.html /var/www/html/
sudo cp style.css /var/www/html/
sudo cp script.js /var/www/html/

The final directory structure was:

/var/www/html/
├── index.html
├── style.css
└── script.js
6. Start Apache

I started the Apache service using:

sudo systemctl start apache2

I verified that Apache was running with:

sudo systemctl status apache2

The service showed:

Active: active (running)
7. Configure Firewall

I allowed HTTP and HTTPS traffic through the Ubuntu firewall:

sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

I also allowed the Apache profile:

sudo ufw allow 'Apache'
8. Configure AWS Security Group

The EC2 Security Group was configured to allow incoming web traffic.

Required inbound rules:

Type	Protocol	Port
HTTP	TCP	80
HTTPS	TCP	443
SSH	TCP	22

SSH should ideally be restricted to your own IP address instead of allowing access from anywhere.

9. Access the Website

After Apache was running and the required network access was configured, I opened the EC2 public IP in a browser:

http://54.145.213.217

The website was successfully displayed in the browser.

## 🔄 Deployment Workflow

Website Source Code
        │
        ▼
     GitHub
        │
        │ git clone
        ▼
   AWS EC2 Instance
        │
        ▼
    Ubuntu Linux
        │
        ▼
     Apache2
        │
        ▼
 /var/www/html
        │
        ▼
   Public Website

## 📚 What I Learned

Through this project, I gained practical experience with:

Creating and managing an AWS EC2 instance
Connecting to a remote Linux server using SSH
Using Linux terminal commands
Working with Git and GitHub
Installing and configuring Apache2
Deploying HTML, CSS, and JavaScript files
Understanding Linux web server directories
Managing services with systemctl
Configuring firewall rules using UFW
Configuring AWS Security Groups
Understanding public and private IP addresses
Hosting a website on a cloud server

## 🔐 Future Improvements

The current deployment uses HTTP and a public IP address. The following improvements could make the deployment more production-ready:

 Configure a custom domain name
 Enable HTTPS using an SSL/TLS certificate
 Use an AWS Elastic IP
 Configure automatic deployment using GitHub Actions
 Restrict SSH access to a specific IP address
 Add AWS monitoring and logging
 Configure Apache virtual hosts
 Add a CI/CD pipeline

## 📸 Project Preview

Live Website

The deployed website is served directly from the AWS EC2 instance using Apache2.

## 🎯 Project Outcome

The main goal of this project was to understand the process of taking a website from a GitHub repository and deploying it to a real cloud server.

Final Result

GitHub → AWS EC2 → Ubuntu → Apache2 → Public Internet → Live Website

The project successfully demonstrates a basic cloud-based static website deployment using AWS EC2.

## 👩‍💻 Author

Shreya Balpande

GitHub: @ShreyaBalpande

⭐ If you found this project useful, feel free to explore the repository and learn from the deployment process.


### One recommendation

For your GitHub README, I would **not include your current EC2 public IP permanently** if you're treating this as a portfolio project. Your public IP can change, and exposing an active server address in a README isn't particularly useful.

A more professional version would eventually look like:

```text
🌐 Live Demo: https://your-domain.com
