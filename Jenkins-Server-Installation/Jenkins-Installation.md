### Install Java

```sh
yum install -y java-11*
```

### Confirm Java Version

```sh
java -version

find / -name java-11* | head -n 4

ls -ltra

vi .bash_profile

JAVA_HOME={output_find_command}

export JAVA_HOME

PATH=$PATH:$JAVA_HOME
# To set it permanently update your .bash_profile

source ~/.bash_profile
```

### Install Jenkins

```sh
yum -y install wget

wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
sudo yum install --nogpgcheck jenkins

```

### Start Jenkins

```sh
# Start jenkins service
systemctl start jenkins

# Setup Jenkins to start at boot,
systemctl enable jenkins
```

### Get the Port on which Jenkins is running 

```sh
netstat -ntlp
```

### Configure Jenkins by Grabing the default password 
  - Password Location:
 ```sh
 cat /var/lib/jenkins/secrets/initialAdminPassword
```
