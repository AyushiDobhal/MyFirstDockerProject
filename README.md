# MyFirstDockerProject
# Used docker-compose
You can use any system that has docker and docker compose installed and are active to run and use this project. 
Below are the steps to install docker and docker compose on RHEL 8.0:

********** install yum **********
1.) Open the folder yum.repos.d
cd /etc/yum.repos.d
2.) Create a repository
vim ayushi.repos
3.) Enter the path for dvd files AppStream and BaseOS
[dvd1]
baseurl=file:///run/media/root/RHEL-8-0-0-BaseOS-x86_64/BaseOS
gpgcheck=0

[dvd2]
baseurl=file:///run/media/root/RHEL-8-0-0-BaseOS-x86_64/AppStream
gpgcheck=0
4.) Initiate the repository
yum.repolist

*************	install docker **************

1.) Create a new repository in yum.repos.d
vim docker.repo
2.) Enter the docker rpm url
[docker]
baseurl=https://download.docker.com/linux/centos/7/x86_64/stable/
gpgcheck=0
3.) Install docker
yum install docker-ce --nobest

************* run docker-compose ***************

1.) Run the below mentioned commands on command line to install docker-compose:
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
2.) Make a seperate workspace/ directory
mkdir /example
3.) Create .yml file
vim docker-compose.yml
4.) Run the file
docker-compose up 

*********** Some networking commands required *************

1.) systemctl enable firewalld
2.) firewall-cmd --zone=public --add-masquerade --permanent
3.) firewall-cmd --zone=public --add-port=80/tcp
4.) firewall-cmd --zone=public --add-port=443/tcp
5.) firewall-cmd --reload
6.) systemctl restart docker

*********** A brief summary of the project *************

Using docker-compose version 3.1, I've tried to utilise the wordpress' functionality of blog creation by connecting it to a MySQL database. I've used wordpress 5.1.1 image supported by PhP 7.3 and MySQL 5.7 to store the user data.  
