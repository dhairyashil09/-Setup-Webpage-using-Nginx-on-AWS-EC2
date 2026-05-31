# Setup Webpage using Nginx on AWS EC2

This project demonstrates how to set up an Nginx web server on an AWS EC2 instance and host a custom webpage using HTML and PHP.

---

# Project Overview

In this project, we:

- Launch an AWS EC2 Linux instance
- Connect to the server using SSH
- Install Nginx, PHP, and MariaDB
- Create an automation shell script
- Configure Nginx
- Deploy a sample webpage
- Verify all services are running successfully

---

# Technologies Used

- AWS EC2
- Amazon Linux 2023
- Nginx
- PHP-FPM
- MariaDB
- Linux Shell Scripting

---

# Step 1: Connect to EC2 Instance

Use SSH to connect to your EC2 instance.

```bash
ssh -i [PRIVATE-KEY] ec2-user@<PUBLIC-IP>
```

---

# Step 2: Create Shell Script File

Create a shell script file named `auto.sh`.

```bash
sudo nano auto.sh
```

## Screenshot

<img width="543" height="108" alt="1" src="https://github.com/user-attachments/assets/10ed5fd1-895e-421f-bd81-123d9d5e94d4" />


---

# 📂 Step 3: Add Automation Commands

Paste the following commands into the script file.

```bash
#!/bin/bash

sudo yum upgrade -y
sudo yum update -y

sudo yum install nginx mariadb105-server php -y

sudo service nginx start
sudo service mariadb start
sudo service php-fpm start

cd /usr/share/nginx/html

sudo touch index.php

echo "<?php phpinfo();?>" | sudo tee index.php
```

## Screenshot


<img width="921" height="210" alt="2" src="https://github.com/user-attachments/assets/dbf18619-8e0c-4ffc-9770-1b0ddb159fd7" />


---

# 📂 Step 4: Give Execute Permission

Make the shell script executable.

```bash
sudo chmod +x auto.sh
```

## Screenshot

<img width="508" height="52" alt="3" src="https://github.com/user-attachments/assets/0b4ee52d-f4a0-44a1-a829-1a2de6d5dcae" />


---

# Step 5: Run the Script

Execute the automation script.

```bash
./auto.sh
```

## Screenshot

<img width="418" height="26" alt="4" src="https://github.com/user-attachments/assets/b2b3b11d-c872-4eee-acae-f1cab9635f4b" />


---

# Step 6: Verify Nginx Service

Check whether Nginx is running properly.

```bash
sudo service nginx status
```

## Screenshot

<img width="1178" height="444" alt="6" src="https://github.com/user-attachments/assets/62568a5e-dbc7-4727-ab92-aad6a776589c" />

---

# Step 7: Verify PHP-FPM Service

Check PHP service status.

```bash
sudo service php-fpm status
```

## Screenshot

<img width="1104" height="387" alt="7" src="https://github.com/user-attachments/assets/5fd69510-cf65-4222-a7da-82eeaa97c2ee" />


---

# Step 8: Verify MariaDB Service

Check MariaDB status.

```bash
sudo service mariadb status
```

## Screenshot

<img width="1366" height="535" alt="8" src="https://github.com/user-attachments/assets/d3e11874-a74c-402e-9b82-6d8ff4f5d071" />

---

# Step 9: Configure Nginx

Open the Nginx configuration file.

```bash
sudo nano /etc/nginx/nginx.conf
```

## Screenshot

<img width="616" height="35" alt="9" src="https://github.com/user-attachments/assets/585e0590-9245-4e5d-8104-23ebcff88b9d" />

---

# Step 10: Add PHP Index File

Inside the server block, update the index configuration.

```nginx
index index.html index.php;
```

## Screenshot

<img width="614" height="352" alt="10" src="https://github.com/user-attachments/assets/e9339f95-6e58-44c4-8544-d50174a797ae" />

---

# Step 11: Restart Services

Restart Nginx and PHP-FPM services.

```bash
sudo service nginx restart
sudo service php-fpm restart
```

## Screenshot

<img width="585" height="80" alt="11" src="https://github.com/user-attachments/assets/666c49ad-9c31-4d29-add3-89f1c4b721ed" />

---

# Step 12: Check AWS EC2 Public IP

Copy the Public IPv4 address from your EC2 dashboard.

## Screenshot

<img width="1489" height="745" alt="12" src="https://github.com/user-attachments/assets/e4d9cdcc-1120-471e-a966-4ff22b9d5b21" />

---

# Step 13: Add Custom HTML file

Navigate to the Nginx HTML directory and Paste given Html code into index.html.

```bash
cd /usr/share/nginx/html/

ls
```
Open Index.html file
```bash
sudo nano index.html

```
Paste the code from the Repository index.html into Nginx index.html

## Screenshot

<img width="779" height="62" alt="13" src="https://github.com/user-attachments/assets/ae0a857b-b5b3-4de5-81d7-53fb6b345c43" />

---

# Step 14: Access the Webpage

Open your browser and enter the EC2 public IP address.

```text
http://<PUBLIC-IP>
```

Your Nginx webpage should display successfully.

## Screenshot

<img width="1723" height="947" alt="15" src="https://github.com/user-attachments/assets/cf4350e8-c4de-402e-88bb-9fdb297e13e4" />

---

# - Output

- Nginx server installed successfully
- PHP configured successfully
- MariaDB service running
- Custom webpage hosted on EC2 instance

