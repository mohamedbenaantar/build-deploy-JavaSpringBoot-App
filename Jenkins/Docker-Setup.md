## Install Docker

```sh
yum install -y docker
systemctl start docker
chkconfig docker on
service docker status
```

## provide permissions to jenkins user in jenkins server to access docker

```sh
cat /etc/group | grep -i docker
sudo usermod -aG docker jenkins
sudo chmod 777 /var/run/docker.sock
```

## Add Jenkins user into sudoers file to get sudo access

```sh
vi /etc/sudoers
jenkins ALL=(ALL) NOPASSWD: ALL
```   
