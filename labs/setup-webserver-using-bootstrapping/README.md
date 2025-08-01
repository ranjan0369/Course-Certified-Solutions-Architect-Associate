# Launching an EC2 Instance with Bootstrap Scripts

Bootstrapping allows you to automate the installation and configuration of software packages at the time of instance launch by passing a user data script. This is a quick guide to **launch an AWS EC2 instance** and **automatically configure a web server** using **User Data (bootstrap scripts)**.

---

## 🚀 Steps

### 1. Launch EC2 Instance
- Use **Amazon Linux 2 (Free Tier Eligible)**.
- Configure the **security group** to allow:
  - **HTTP (80)**
  - **SSH (22)**

---

### 2. Add Bootstrap Script in User Data
Add the following script during **instance launch** under **Advanced → User Data**:

```bash
#!/bin/bash
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo yum install -y git
cd /var/www/html
echo "<h1>Hello from EC2 Bootstrap!</h1>" > index.html
sudo service httpd start

```

This will:

-   Install **Apache web server**
    
-   Start it on boot
    
-   Serve a simple webpage
    

----------

### 3. Access Your Web Server

1.  Copy the **Public IPv4 Address** of your EC2 instance.
    
2.  Open in a browser:
    

```
http://<your-ec2-public-ip>

```

----------

### 4. Cleanup

Terminate the instance after testing to **avoid AWS charges**.

----------

For the detailed walkthrough, check my [Medium Post](https://medium.com/@ranjansth1996/launching-ec2-with-bootstrap-scripts-set-up-a-web-server-in-minutes-a55e1487def5).