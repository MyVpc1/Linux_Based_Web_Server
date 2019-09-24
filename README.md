# Linux Based Web Server Configure
In this project, we will develop a Linux based web server that contains LEMP (Linux, Engine-X, MySQL, PHP) As an Operating System we chose Linux based OS Ubuntu 19.04. We also chose NGINX as Web Server which is modern and packed with cutting edge technology include load balancer. MySQL as Database System and Server Side Script PHP.
[Project Website Link](https://sites.google.com/view/lemp)

![Linux based web server lemp](https://i.imgur.com/DvpzFJ5.png?1)

## Task List  
1. Update Packages for Linux OS 
2. Install The NGINX Web Server
3. Install MySQL
4. Install PHP
5. Congigure PHP
6. Configure NGINX

## Let’s start off with updating all the upgradable packages.
### Update Packages for Linux OS:

```bash
sudo apt-get update
sudo apt-get upgrade -y
```
### Install the latest version of Nginx on Ubuntu using the following command:
```bash
sudo apt-get install nginx
```
### Now run below command to restart nginx for the first time:

```bash
sudo service nginx restart
```
### Enable HTTP for NGINX Server
```bash
sudo ufw allow 'Nginx HTTP'
```
### You can verify the change by running:
```bash
sudo ufw status
```
### This command’s output will show that HTTP traffic is allowed:
```bash
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
Nginx HTTP                 ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
```
### Run Nginx check :
```bash
Just open your browser and type http://localhost/
```
### Step 2: Install MySQL to Manage Site Data
```bash
sudo apt-get install mysql-server
```
### Now, let’s secure the MySQL installation by running the following security script command:
```bash
sudo mysql_secure_installation
```
### Check MySQL
```bash
sudo mysql
```
### Next, check which authentication method each of your MySQL user accounts use with the following command:
```sql
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
### Output
```sql
+------------------+-------------------------------------------+-----------------------+-----------+
| user             | authentication_string                     | plugin                | host      |
+------------------+-------------------------------------------+-----------------------+-----------+
| root             |                                           | auth_socket           | localhost |
| mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| debian-sys-maint | *CC744277A401A7D25BE1CA89AFF17BF607F876FF | mysql_native_password | localhost |
+------------------+-------------------------------------------+-----------------------+-----------+

```