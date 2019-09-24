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
### Exit form MySQL
```mysql
exit
```
### Install PHP for Processing
```bash
sudo add-apt-repository universe
```
### Install the php-fpm module along with an additional helper package, php-mysql.
```bash
sudo apt install php-fpm php-mysql
```
### Configure the PHP Processor
```bash
sudo nano /etc/php/7.0/fpm/php.ini
```
### We will change both of these conditions by uncommenting the line and setting it to "0" like this:
```bash
cgi.fix_pathinfo=0
```
### Now, we just need to restart our PHP processor by typing:
```bash
systemctl restart php7.0-fpm
```
### Configure Nginx to Use the PHP Processor
```bash
sudo nano /etc/nginx/sites-available/default
```
##### By editing a new server block configuration file, rather than editing the default one, you’ll be able to easily restore the default configuration if you ever need to. Add the following content, which was taken and slightly modified from the default server block configuration file, to your new server block configuration file:

```bash
server {
        listen 80;
        root /var/www/html;
        index index.php index.html index.htm index.nginx-debian.html;
        server_name example.com;

        location / {
                try_files $uri $uri/ =404;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }
}
```
### Set your configuration file for syntax errors by typing:
```bash
sudo nginx –t
```
### Reload Nginx to make the necessary changes:
```bash
sudo systemctl reload nginx
```
### Create a PHP File to Test Configuration:
```bash
 nano /var/www/html/info.php
```
### Type or paste the following lines into the new file. This is valid PHP code that will return information about our server:
```php
?php
phpinfo();
?
```
## Final Check :
```url
http://localhost/info.php
```

![PHP Info page](https://i.imgur.com/PJIL5Hn.png?1)