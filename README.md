# Linux Based Web Server Configure
In this project, we will develop a Linux based web server that contains LEMP (Linux, Engine-X, MySQL, PHP) As an Operating System we chose Linux based OS Ubuntu 19.04. We also chose NGINX as Web Server which is modern and packed with cutting edge technology include load balancer. MySQL as Database System and Server Side Script PHP.
[Project Website Link](https://sites.google.com/view/lemp)

![Linux based web server lemp](https://i.imgur.com/DvpzFJ5.png?1)

## Task List  
1. Update Packages for Linux OS 
2. Install NGINX
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
### Run Nginx check :
```
Just open your browser and type http://localhost/
```
### Let’s add the MySQL 8.0 into our apt repository running the below command:
```bash
wget –c https://dev.mysql.com/get/mysql-apt-config_0.8.10-1_all.deb
```
### Now configure the MySQL package using dpkg command:
````bash
sudo dpkg -i mysql-apt-config_0.8.10-1_all.deb
```