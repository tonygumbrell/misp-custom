# misp-custom

All images are built from https://github.com/MISP/misp-docker and customised to support systems where internet connectivity is limited. This method requires the download of only 2 images and a folder structure to import from github, or manually copied into your environment.

Build Process.

On a CentOS Base Build:

1) yum install docker
2) yum install epel-release
3) yum install python-pip
4) yum install git
5) pip install docker-compose
6) docker pull tonygumbrell/misp-web:xx
7) docker pull tonygumbrell/misp-db:xx
- Make sure matching versions are used
- For version descriptions see the Dockerhub repo descriptions.
8) git clone https://github.com/tonygumbrell/misp-custom.git
9) cd misp-custom > cd misp-docker
10) edit docker-compose.yaml and update the image names and versions. Update all the passwords within docker-compose.yml to a secure set.
11) docker-compose up
12) once the containers are built docker-compose start/stop is sufficient.
13) To update the misp db user password, login to the misp-db container with 'docker exec -it misp-db /bin/bash' 
  - run 'mysql -u misp -p Passw0rds123!'
  - run 'set password = PASSWORD('newpassword_matches_step_9');'
14) login to the misp-web container with 'docker exec -it misp-web /bin/bash'
15) run the following 'mysql -u misp --password=XXXXXX misp -P 3306 2>&1 < /var/www/MISP/INSTALL/MYSQL.sql'
16) update /var/www/MISP/app/Config/config.php with an updated baseurl
17) update /var/www/MISP/app/Config/database.php with a revised hostname, username, password for the mysql db

All done, you should now be able to browse to http://x.x.x.x and login with the default MISP credentials of admin@admin.test / admin


