# cloud-engineering-examproject
server provisioning and html page deployment for cloud engineering 2nd semester project 
Cloud Engineering 2nd Semester Project: Server Provisioning and HTML Deployment

A clear, step-by-step documentation of how I provisioned the server, installed the web server, deployed the HTML page, and configured networking.

1. Provisioning the Server

1.1. Set Up an Ubuntu Linux Server on AWS

1. Log into AWS Console: I logged into the AWS Management Console. Then, I navigated to EC2 under the "Compute" section.


2. Launch a New EC2 Instance: I clicked on Launch Instance.

I chose an Ubuntu AMI (e.g., Ubuntu 22.04 LTS).

I selected the Instance Type as t3.micro for the free tier.

I left the instance configuration as default.

In Security Groups, I allowed HTTP traffic (port 80) and SSH (port 22).

I selected a Key Pair to download for SSH access and ensured the .pem file was stored securely.



3. Access the EC2 Instance: After the instance started, I found the Public IP address of the instance. I used the following SSH command to access the server:

ssh -i /path/to/your/key.pem ubuntu@<16.170.229.55>



2. Installing the Web Server (Apache)

2.1. Install Apache Web Server

1. Update the System: I updated the system with:

sudo apt update && sudo apt upgrade -y


2. Install Apache: I installed the Apache web server using the command:

sudo apt install apache2 -y


3. Start and Enable Apache Service: I started Apache with:

sudo systemctl start apache2

And enabled it to start on boot with:

sudo systemctl enable apache2


4. Allow HTTP Traffic through the Firewall: I allowed HTTP traffic using ufw:

sudo ufw allow 'Apache'



2.2. Verify Apache Installation

To verify, I opened a browser and entered the Public IP of my instance (e.g., http://<16.170.229.55 >). I saw the Apache default page, confirming that Apache was installed and running.

3. Deploying the HTML Page

3.1. Create and Deploy the HTML Page

1. Navigate to the Web Directory: Apache serves content from the /var/www/html directory. So, I changed to this directory:

cd /var/www/html


2. Create the HTML File: I used nano to create index.html:

sudo nano index.html


3. Add HTML Content: I added the following HTML code into index.html (modified with my actual details):

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to Chioma's Landing Page</title>
</head>
<body>
    <h1>Welcome to Chioma's Landing Page</h1>
    <p>Hello! My name is Chioma Victoria Odezue, and I am a passionate cloud engineer in training. I'm excited to showcase my abilities and demonstrate how we can build amazing solutions together.</p>
    
    <h2>About Me</h2>
    <ul>
        <li>Registered BSN Nurse</li>
        <li>Social Media Manager and Website Designer</li>
        <li>Student at AltSchool Africa, Cloud Engineering Program</li>
        <li>Believer and Wife</li>
    </ul>

    <h2>About This Project</h2>
    <p>This project demonstrates my ability to deploy a web application using AWS EC2. The webpage serves as a simple landing page, combining HTML skills and cloud knowledge. It highlights my learning journey at AltSchool Africa as I continue to grow in cloud engineering.</p>

    <footer>
        <p>Contact me: nwankwochioma407@gmail.com</p>
    </footer>
</body>
</html>


4. Save and Exit: To save the file, I pressed CTRL + X, then Y, and hit Enter.



3.2. Verify the HTML Page

I opened a browser and entered the Public IP of my instance (e.g., http://<16.170.229.55 ), and I saw my HTML page displaying the information I added.

4. Configuring Networking

4.1. Configure Security Group for HTTP Traffic

1. In the AWS EC2 Console, I navigated to Security Groups.


2. I found the security group associated with my instance and edited the inbound rules to allow HTTP traffic on port 80.



4.2. Access the Web Page

I accessed my web page in a browser by entering the Public IP of my instance (e.g., http://<16.170.229.55>), and the page loaded correctly.

4.3. Configure a Domain Name (Optional)
If I wanted to use a domain name instead of the IP address, I would:

1. Register a domain name through a DNS provider (e.g., Route 53 in AWS or GoDaddy). But i used self assigned certificate.


2. Set an A record to point to the EC2 instance’s Public IP.



5. Final Documentation

5.1. GitHub Repository Documentation

In my README.md of the GitHub repository, I documented the following:

# Cloud Engineering 2nd Semester Project

## 1. Provisioned Server
- Provisioned an Ubuntu Linux server on AWS EC2.
- Public IP: <16.170.229.55>

## 2. Web Server Setup
- Installed Apache web server on the EC2 instance.
- Configured Apache to serve content from /var/www/html.

## 3. HTML Page
- Created a simple landing page with the following details:
  - Name: Chioma Victoria Odezue
  - Project Title: Cloud Engineering Prototype
  - Brief Description of the project and bio.

## 4. Networking Configuration
- Configured security groups to allow HTTP traffic on port 80.
- Verified the webpage by accessing http://<16.170.229.55>.

## 5. Access the Website
- Visit the website via: http://16.170.229.55          <https://16.170.229.55>

This is the documentation details on how I provisioned the server, set up Apache, deployed the HTML page, and configured the networking. I've also included the steps for using a domain name if needed.