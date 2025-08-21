blog
==============

# install

```
sudo rm -rf /var/www/blog
nano blog-ssl.conf
sudo cp blog-ssl.conf /etc/apache2/sites-available/blog-ssl.conf; sudo a2ensite blog-ssl; sudo service apache2 restart
sudo certbot --apache -d blog.chrismurray.co.uk -d www.blog.chrismurray.co.uk --agree-tos --renew-by-default --no-redirect
```

## set up MySQL database

```
sudo mysql -u root
CREATE DATABASE `blog` CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE USER 'blog'@'localhost' IDENTIFIED WITH caching_sha2_password BY '';
GRANT ALL PRIVILEGES ON `blog` . * TO 'blog'@'localhost';
FLUSH PRIVILEGES;
quit
```

## wget instructions

```
sudo rm -rf latest.tar.gz wordpress /var/www/blog
wget https://wordpress.org/latest.tar.gz; tar -xzvf latest.tar.gz; rm latest.tar.gz
nano wordpress/wp-config-sample.php; cp wordpress/wp-config-sample.php wordpress/wp-config.php
sudo cp -r wordpress/ /var/www/blog; sudo chown www-data -R /var/www
sudo cp -r /var/www/html/.well-known/ /var/www/blog/.well-known; sudo chown www-data -R /var/www
```
