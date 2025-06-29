docker: docker is a tool that allow you to build, deploy and run applications
        in an isolated and consistent enviroment across different machines

///////////////////////////////////////////

docker-compose: a tool that simplifies deployment of multi-container docker
                applications, it can configure each service setting like the
                image to use or the ports to expose

it is composed of three parts: Services - Networks - Volumes

driver: local : create the volume on the same docker host where you run the container

Bridge network: are the default for single-host container comunication, is suitable where containers need to comunicate with one host like the microservices architecture

//////////////////////////////////////////

docker secrets: is used to menage sensitive data that should not be stored uncrypted, it add a layer of abstraction between the container and a set of credentials

///////////////////////////////////////////

server setup:
        add docker official GPG key
        add docker repository
        

# configure nginx and php to communicate

- Default config for PHP location: 
        /etc/php/8.2/fpm/pool.d/www.conf

- Default config for NGINX location: 
        /etc/nginx/sites-available/default

docker cp wp-php:/etc/php/8.2/fpm/pool.d/www.conf ./requirements/wordpress/.
docker cp nginx:/etc/nginx/sites-available/default ./requirements/nginx/.

For the php default configuration file “www.conf” we only need to change a single line (line 41). Instead of listening to the default “/run/php/php8.2-fpm.sock address, we need to tell php that it needs to accept FastCGI request from address “wp-php:9000”, the localhost of our wordpress-php container at port 9000.

For the nginx default configuration file “default”…
… we first need to uncomment the block that allows nginx to pass PHP scripts to the FastCGI server. (uncomment line 56 to 63).
Then comment the parth where nginx uses the unix socket as a fastcgi_pass argument and modify the other one that is using tcp sockets from 127.0.0.1:9000 to wp-php:9000.
Now our nginx knows where to send php files for processing.

One more thing in this configuration file is adding index.php to the list of indexes at line 44.

After we save both of these config files with the modifications made, we need to copy them inside the containers.