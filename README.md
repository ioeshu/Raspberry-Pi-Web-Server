# Turn Raspberry Pi Into Web Server

![Project Image](https://technuws.com/wp-content/uploads/2020/09/install-Raspbian.jpg)

> This project helps you to turn your Raspberry Pi into a personal web server. 

---

### Table of Contents
After your personal web server is complete, you can use it to host a custom HTML or PHP resume, or a wordpress site on your Raspberry pi

- [Description](#description)
- [How To setup ](How-To-setup )
- [Run Wordpress on Raspberry pi ](#Run-Wordpress-on-Raspberry-pi)
- [Run PHP or Html script on Raspberry pi](#Run-PHP-or-Html-script-on-Raspberry-pi)

- [Author Info](#author-info)

---

## Description

You can use google cloud or Amazon Aws to host your script but if you like building things this project for you.  

#### RUN PHP SCRIPT / WORDPRESS ON RASPBERRY PI 

- Run Wordpress on Raspberry pi 
- Run PHP or Html script on Raspberry pi

---

## How To setup 
## Run Wordpress on Raspberry pi
### Installation

- Install Apache

```html
    sudo apt-get install apache2 -y
```
- Install PHP

```html
    sudo apt install php libapache2-mod-php -y
```
- Install MariaDB

```html
    sudo apt-get install mariadb-server php-mysql -y 

    sudo service apache2 restart
```

- Download WordPress
### Change directory to `/var/www/html/` and delete all the files in the folder.

```html
cd /var/www/html/
sudo rm *
```
Download WordPress using wget.
```html
sudo wget http://wordpress.org/latest.tar.gz
```
Extract, Move , remove tarball
```html
sudo tar xzf latest.tar.gz
sudo mv wordpress/* .
sudo rm -rf wordpress latest.tar.gz
```

change the ownership of all these files to the Apache user:
```html
sudo chown -R www-data: .
```

### Set up WordPress Database
- Set up MySQL/MariaDB
```html
sudo mysql_secure_installation
```
- Create the WordPress database
```html
sudo mysql -uroot -p
create database wordpress;
```
If this has been successful, you should see this: `Query OK, 1 row affected (0.00 sec)`

Now grant database privileges to the root user. Note: you will need to enter your own password after `IDENTIFIED BY`.
```html
GRANT ALL PRIVILEGES ON wordpress.* TO 'root'@'localhost' IDENTIFIED BY 'ENTER-YOUR-PASSWORD';
```
For the changes to take effect, you will need to flush the database privileges after that exit `Ctrl + D.` and then reboot

```HTML
FLUSH PRIVILEGES; 
```
### WordPress configuration
```html
http://localhost
```
keep it like this 
```html
Database Name:      wordpress
User Name:          root
Password:           <YOUR PASSWORD>
Database Host:      localhost
Table Prefix:       wp_
```

#### Click Submit to proceed.
#### Click the Run the install button.

## Run PHP or Html script on Raspberry pi

- Install Apache

```html
    sudo apt-get install apache2 -y
```
- Install PHP

```html
    sudo apt install php libapache2-mod-php -y
```
Test the web server
```html
http://localhost/ or http://Enter your ip address
```

you will see a default web page is just an HTML file on the filesystem. It is located at
`/var/www/html/index.html`

Navigate to this directory, remove the file and create a new php file

```html 
cd /var/www/html
sudo rm index.html
sudo nano index.php
```

paste and click `Ctrl+ O` 
```html
<?php echo "hello world"; ?>
```


---


## Author Info

- Twitter - [@Eswar](https://twitter.com/IAm_Eswar)
- Website - [TechNuws](https://technuws.com)

[Back To The Top](#Turn-Raspberry-Pi-Into-Web-Server)
