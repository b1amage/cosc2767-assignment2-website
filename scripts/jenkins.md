# Setup EC2

## Install stuff

```bash
#!/bin/bash
sudo su -
yum install git -y

# install jdk
sudo amazon-linux-extras install java-openjdk11 -y

# change directory to opt
cd /opt

# install maven
wget https://dlcdn.apache.org/maven/maven-3/3.9.5/binaries/apache-maven-3.9.5-bin.tar.gz

# extract compressed maven file
tar -xvzf apache-maven-3.9.5-bin.tar.gz

# rename it for rememberable name
mv apache-maven-3.9.5 maven

# install jenkins
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
yum install jenkins
```

- Run `service jenkins start`

- Get password on jenkins instance `/var/lib/jenkins/secrets/initialAdminPassword`
