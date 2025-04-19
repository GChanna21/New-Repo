
# Three Tier Application

A brief description of what this project does and who it's for



## Screenshots
<img src=""https://github.com/GChanna21/New-Repo/blob/main/Screenshot%20(5).png?raw=true ="">



## Installation

Install my-project with npm

```bash
sudo apt update
```
## WEB Tier Configuration
```bash
sudo apt update
sudo apt install apache2 -y
sudo a2enmod proxy
sudo a2enmod proxy_http
```
## Apache Config (Proxy to App Tier):
creating Configuration file
```bash
sudo nano /etc/apache2/sites-available/orangehrm.conf
```
### Add this in orangehrm.conf
```bash
<VirtualHost *:80>
    ServerAdmin <channachanna9880@gmail.com>
    ServerName <Web Tier Public ip>

    ProxyPreserveHost On
    ProxyPass / http://App Tier Pub IP/orangehrm/
    ProxyPassReverse /App Tier Pub IP/orangehrm/

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

## APP Tier Configuration
update and apache2 along with PHP
```bash
sudo apt update
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:ondrej/php -y
sudo apt update

# Install Apache2, PHP 8.1, and required modules
sudo apt install apache2 php8.1 libapache2-mod-php8.1 php8.1-mysql php8.1-xml php8.1-curl php8.1-zip php8.1-mbstring php8.1-intl unzip -y
```
Download orangehrm Entire Package
```bash
wget https://sourceforge.net/projects/orangehrm/files/stable/5.5/orangehrm-5.5.zip/download -O orangehrm-5.5.zip
```
Unzip Package
``` bash
unzip orangehrm-5.5.zip
```
Move Rename Move Package to location
```bash
sudo mv orangehrm-5.5 /var/www/html/orangehrm
```
Providing Permission For orangehrm
```bash
sudo chown -R www-data:www-data /var/www/html/orangehrm
```
restart Apache2
```bash
sudo systemctl restart apache2
```
## Documentation

📦 What We'll Do:
Install Apache

Install MySQL

Install PHP

Configure Apache + PHP

Download & deploy OrangeHRM

Set up the database

Finalize OrangeHRM setup in the browser


## Demo


## Features

- Light/dark mode toggle
- Live previews
- Fullscreen mode
- Cross platform


## Feedback

If you have any feedback, please reach out to us at fake@fake.com


## Roadmap

- Additional browser support

- Add more integrations


![Logo](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/th5xamgrr6se0x5ro4g6.png)


## Badges

Add badges from somewhere like: [shields.io](https://shields.io/)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)


## Usage/Examples

```javascript
import Component from 'my-project'

function App() {
  return <Component />
}
```

