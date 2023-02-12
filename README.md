# Build-WordPress-with-MySQL
You can build a WordPress website with MySQL using the following steps:
Launch a new EC2 instance and install Docker on it.

Create a Docker network for your WordPress and MySQL containers.

Create a Docker volume to store the WordPress files and MySQL database.

Download the latest version of WordPress and MySQL images from Docker Hub.

Launch a new container from the WordPress image and mount the volume to it.

Launch a new container from the MySQL image and mount the volume to it.

Connect the WordPress container to the Docker network and link it to the MySQL container.

Access the WordPress website and run the setup wizard to configure the database connection.

Customize the website and install plugins and themes as needed.

Here is an example of the Docker Compose file you can use to automate the steps:


version: '3'
services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: password
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: password

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: password
volumes:
    db_data:


