
# deploying_laravel_in_ubuntu_server
install vim
#### =>sudo apt install vim

first step check the server is 18.0 or not
#### => sudo apt update
#### =>sudo apt install apache2 -y

check the firewall about the apache
#### =>sudo ufw app list

include the "Apache Full" to the ufw (unified firewall)
#### =>sudo ufw app info "Apache Full"

allow the apache2 in ufw
#### =>sudo ufw allow in "Apache Full"

install curl
#### =>apt install curl

check the localhost
#### =>curl localhost // curl http://<your_ip>
this should give you the default apache page

install mysql server
#### =>sudo apt install mysql-server

then configure with this command and set admin password
#### =>sudo mysql_secure_installation

check with this command
#### =>sudo mysql
it will give you the mysql shell

include  a private repolist

#### => sudo add-apt-repository ppa:ondrej/php

most impoerant
update your repository
#### =>apt update

install php7.2
#### =>sudo apt-get install php7.2

check the version with this command
#### =>php -v

go to  /var/www/html
#### =>cd /var/www/html

and delete everything inside the html folder .dont delete the html folder
inside the html foldergo to
#### => rm -rf * 

create the file
#### => vim index.php

write this line
####  <?php phpinfo() ?>
 
 save and exit
 
####  => curl localhost
 
you should see the php information
 
install php module
####  => sudo apt install php7.2-opcache php7.2-mbstring php-memcached
####  => sudo apt install php7.2-zip
####  => sudo apt install php7.2-xml
 
install php mysql module
####  =>sudo apt-get install php7.2-mysql php7.2-soap
 
install composer

go to the home directory

download the composer file
####  => php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

install wget
####  =>apt isntall wget -y

import the hash file 
####  => HASH="$(wget -q -O - https://composer.github.io/installer.sig)"

verify the installation
####  => php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"


if everything ok then this message will show

Installer verified

install the composer

####  => sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

test the composer with
####  => composer

install laravel

####  => sudo  composer global require laravel/installer

the laravel command wil save in the ~/.composer/vendor/bin/ dirctory

create an alias in the bashrc file [you can also add the path]

####  => vim ~/.bashrc

add this line exactly 
after the pound sign
####  alias laravel='~/.composer/vendor/bin/laravel'

go to the /var/www/html

#### =>laravel .new 

it will create the application
then 

#### => npm install


Create a user in the database 

#### =>sudo mysql

#### mysql>CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
#### mysql>GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost';
#### mysql>FLUSH PRIVILEGES;



create a database 'test' you can give any name

#### mysql>create database test;

exit from mysql

go to application folder

#### =>vim .env

edit the 

#### USERNAME=newuser
#### PASSWORD=password
#### DATABASE=test

then save and exit

=>enter the command 
#### =>php artisan migrate

very important 

in the applciation folder there is a file name server.php
change the name to index.php

#### => mv server.php index.php

then reload the server

#### =>service apache2 restart

go to your ip address in the browser

#### http://<your ip>
 
this it

