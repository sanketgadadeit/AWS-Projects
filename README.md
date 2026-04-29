## Introduction
This project demonstrates the deployment of a WordPress website on a cloud environment using AWS. It covers setting up a web server, database configuration, and hosting a fully functional dynamic website.

## Architecture
![alt text](image.png)

## Step by step explaination how to deploye wordpress website
 
 ### Step1: Create a Instance
 ![](./Screenshot%20(97).png)

 ### Step2: update a instance and install services and run it using shellscript
 ![](./Screenshot%20(98).png)

 ### run .sh file
 ![](./Screenshot%20(99).png)

 ### Step 3: Ensure all service are running using 
 sudo systemctl status "services names"
 ![](./Screenshot%20(100).png)

 #### See apache user created by the system 
 ![](./Screenshot%20(102).png)

 ### Step 4: We have to install Package php8.5-mysqlnd.x86_64<br>
 This is the connector between php and mysql
 ![](./Screenshot%20(104).png)

 ### Step 5:  Get the website link from wordpress using wget "url"
 ![](./Screenshot%20(105).png)

 ### Step 6: lates untar the the .tar file 
 ![](./Screenshot%20(106).png)
 ![](./Screenshot%20(108).png)

### Step 7 : Create a Database and wordpress can automatically create a table and add data 
![](./Screenshot%20(110).png)

### Step 8: go to the browser and check for the access using your_ip/wordpress/
here you see this page click on let's go
![](./Screenshot%20(111).png)

### Step 9: Add info and click on submit
![](./Screenshot%20(112).png)

### Step 10: Here wordpress uable to get the access of /wordpress in the /var/www/html
![](./Screenshot%20(113).png)

### Step 11: check the permissions of wordpress 
![](./Screenshot%20(114).png)

### Step 12: change the permission of wordpress
![](./Screenshot%20(115).png)

### Step 13: now refresh or resubmit it
![](./Screenshot%20(116).png)
![](./Screenshot%20(117).png)

### Step 14: click on run the installation and fill the form
![](./Screenshot%20(118).png)
![](./Screenshot%20(119).png)

### Step 15: once it success login as a admin using root
![](./Screenshot%20(120).png)
![](./Screenshot%20(121).png)

### Step 16: See in the database changes done by wordpress
![](./Screenshot%20(122).png)

### Step 17: after this you can add the blog in it and publish it
![](./Screenshot%20(123).png)
![](./Screenshot%20(124).png)

### Step 18: See your Blog is published
![](./Screenshot%20(125).png)
