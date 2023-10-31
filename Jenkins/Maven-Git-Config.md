# Install and Configure Maven & git in Jenkins server

## Install Maven

```sh
yum install wget

cd /opt/

wget https://dlcdn.apache.org/maven/maven-3/3.9.5/binaries/apache-maven-3.9.5-bin.tar.gz

# Extract the tar file
tar -xvzf apache-maven-3.9.5-bin.tar.gz

cd /root/

vi .bash_profile

export M2_HOME=/opt/apache-maven-3.9.5

export M2=$M2_HOME/bin

PATH=$PATH:$M2

# Update the bash_profile without logout and login again
source ~/.bash_profile
```

## Check the Installation
```sh
mvn version
```

## Install Git
```sh
yum install -y git
```

## Assign shell to jenkins user
```sh
vi /etc/passwd
change shell from /bin/false to /bin/bash
```
