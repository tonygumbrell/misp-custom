# misp-custom

All images are built from https://github.com/MISP/misp-docker and customised to support systems where internet connectivity is limited

Build Process.

On a CentOS Base Build:

1) yum install docker
2) yum install epel-release
3) yum install python-pip
4) pip install docker-compose
5) docker pull tonygumbrell/misp-web:xx
6) docker pull tonygumbrell/misp-db:xx
- Make sure matching versions are used
- For version descriptions see the Dockerhub repo descriptions.
7) Import the misp-docker folder. 
8) Edit the docker-compose.yaml file and update the image names
9) 


