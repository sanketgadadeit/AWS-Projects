#  Static Website Deployment on Nginx (Ubuntu)

##  Project Description
This project demonstrates how to deploy a static website using Nginx on an Ubuntu server. It includes installation, configuration, and hosting of a website accessible via a web browser.

---

##  Tech Stack
- Ubuntu Linux
- Nginx Web Server
- HTML, CSS

## Architecture
![alt text](image.png)
---

##  Step-by-Step Implementation
### Create Instance
![](./Screenshot%20(168).png)
### 1. Update System Packages
sudo apt update 
![](./Screenshot%20(169).png)
### 2. Install Nginx
sudo apt install nginx -y
![](./Screenshot%20(170).png)
### 3. Start and Enable Nginx
sudo systemctl start nginx
sudo systemctl enable nginx

### 4. Verify Nginx Status
sudo systemctl status nginx
![](./Screenshot%20(172).png)
### 5. Deploy Website Files
cd /var/www/html
sudo rm index.nginx-debian.html
## Upload your static website files here, i downloded static page usin wget 
![](./Screenshot%20(174).png)



### 7. Restart Nginx
sudo systemctl restart nginx

---

##  Access the Website

![](./Screenshot%20(175).png)


##  Features
- Fast and lightweight web server
- Easy configuration
- Efficient static content delivery

---

##  Learning Outcomes
- Nginx installation and configuration
- Linux file handling
- Static website hosting

## Conclusion
Successfully deploying a static website on Nginx using Ubuntu demonstrates how efficiently a web server can host and serve content. This process highlights key skills like server configuration, file management, and basic deployment practices. Overall, it provides a strong foundation for real-world web hosting and DevOps workflows.