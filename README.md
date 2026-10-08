# 🌐 Static Website Deployment on AWS EC2

## 📌 Project Overview

This project demonstrates how I deployed a static website on an **AWS EC2 instance** using **Ubuntu Linux and Apache2**.

The website source code was stored in a GitHub repository, cloned onto the EC2 server, and configured to be served publicly through the Apache web server.

This project helped me understand the basics of **cloud computing, Linux server management, Git/GitHub, web servers, networking, and website deployment**.

---

## 🚀 Live Website

The website was deployed on an AWS EC2 instance and accessed through its public IPv4 address.

**Deployment URL:**

http://54.145.213.217

> **Note:** The public IP address may change if the EC2 instance is stopped and started unless an Elastic IP is configured.

---

## 🛠️ Technologies Used

- ☁️ AWS EC2
- 🐧 Ubuntu Linux
- 🌐 Apache2 Web Server
- 🔧 Git & GitHub
- 💻 HTML5
- 🎨 CSS3
- ⚙️ JavaScript
- 🖥️ Linux Terminal
- 🔥 UFW Firewall

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
```

---

# 📋 Deployment Steps

## 1. Launch an EC2 Instance

I created an EC2 instance on AWS with the following configuration:

| Configuration | Details |
|---|---|
| Instance Type | `t2.micro` |
| Operating System | Ubuntu Linux |
| Region | `us-east-1` |
| Instance State | Running |

The EC2 instance acts as the cloud server for hosting the website.

---

## 2. Connect to the EC2 Instance

After launching the instance, I connected to it using SSH and accessed the Ubuntu terminal.

```bash
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

---

## 3. Clone the GitHub Repository

I used Git to download the website source code onto the EC2 server.

```bash
git clone https://github.com/ShreyaBalpande/AWS_ec2.git
```

The repository contains the main website files:

```text
index.html
style.css
script.js
```

---

## 4. Install Apache2

Apache2 was installed as the web server.

```bash
sudo apt update
sudo apt install apache2 -y
```

Apache is responsible for serving the website files to visitors over HTTP.

---

## 5. Copy Website Files to Apache's Web Directory

Apache's default web directory on Ubuntu is:

```text
/var/www/html
```

I copied my website files into this directory:

```bash
sudo cp index.html /var/www/html/
sudo cp style.css /var/www/html/
sudo cp script.js /var/www/html/
```

The final directory structure was:

```text
/var/www/html/
├── index.html
├── style.css
└── script.js
```

---

## 6. Start Apache

I started the Apache service using:

```bash
sudo systemctl start apache2
```

I verified that Apache was running with:

```bash
sudo systemctl status apache2
```

The service showed:

```text
Active: active (running)
```

This confirmed that the Apache web server was successfully running on the EC2 instance.

---

## 7. Configure the Firewall

I allowed HTTP and HTTPS traffic through the Ubuntu firewall:

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

I also allowed the Apache profile:

```bash
sudo ufw allow 'Apache'
```

---

## 8. Configure AWS Security Group

The EC2 Security Group was configured to allow incoming web traffic.

### Required Inbound Rules

| Type | Protocol | Port |
|---|---|---:|
| HTTP | TCP | 80 |
| HTTPS | TCP | 443 |
| SSH | TCP | 22 |

> **Security Note:** SSH access should ideally be restricted to your own IP address instead of allowing access from anywhere.

---

## 9. Access the Website

After Apache was running and the required network access was configured, I opened the EC2 public IP in a web browser:

```text
http://54.145.213.217
```

The website was successfully displayed in the browser.

---

# 🔄 Deployment Workflow

```text
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
```

---

# 📸 Project Screenshots

## AWS EC2 Instance

The EC2 instance is running successfully with the required status checks passed.

![AWS EC2 Instance](images/ec2-instance.png)

---

## Apache2 Web Server

Apache2 was successfully installed and configured on the Ubuntu EC2 instance.

![Apache2 Running](images/apache-running.png)

---

## Live Website

The website was successfully deployed and accessed through the EC2 public IP address.

![Live Website](images/live-website.png)

---

# 📚 What I Learned

Through this project, I gained practical experience with:

- Creating and managing an AWS EC2 instance
- Connecting to a remote Linux server using SSH
- Using Linux terminal commands
- Working with Git and GitHub
- Installing and configuring Apache2
- Deploying HTML, CSS, and JavaScript files
- Understanding Linux web server directories
- Managing services using `systemctl`
- Configuring firewall rules using UFW
- Configuring AWS Security Groups
- Understanding public and private IP addresses
- Hosting a website on a cloud server

---

# 🔐 Future Improvements

The current deployment uses HTTP and a public IP address. The following improvements could make the deployment more production-ready:

- [ ] Configure a custom domain name
- [ ] Enable HTTPS using an SSL/TLS certificate
- [ ] Use an AWS Elastic IP
- [ ] Configure automatic deployment using GitHub Actions
- [ ] Restrict SSH access to a specific IP address
- [ ] Add AWS monitoring and logging
- [ ] Configure Apache Virtual Hosts
- [ ] Add a CI/CD pipeline

---

# 🎯 Project Outcome

The main goal of this project was to understand the process of taking a website from a GitHub repository and deploying it to a real cloud server.

### Final Result

```text
GitHub
   ↓
AWS EC2
   ↓
Ubuntu Linux
   ↓
Apache2
   ↓
/var/www/html
   ↓
Public Internet
   ↓
🌐 Live Website
```

The project successfully demonstrates a basic **cloud-based static website deployment using AWS EC2**.

---

# 👩‍💻 Author

**Shreya Balpande**

GitHub: [@ShreyaBalpande](https://github.com/ShreyaBalpande)

---

⭐ If you found this project useful, feel free to explore the repository and learn from the deployment process.
