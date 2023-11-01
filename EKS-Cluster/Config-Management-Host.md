## From the Management host we are going to create, manage and delete the EKS Cluster

## 1. Create an EC2 Instance with the default config

## 2. Connect to the Instance 

```sh
chmod 400 jenkins-serv.pem
ssh -i "jenkins-serv.pem" ec2-user@ec2-54-80-131-77.compute-1.amazonaws.com
```

## 3. Connect as a Root User

```sh
sudo su -
```

## 4. Follow the Pre-requisites to create an EKS Cluster

https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html

## Start with the Kubectl tool
```sh
# Download the kubectl binary for the cluster's Kubernetes version from Amazon S3
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.28.2/2023-10-17/bin/linux/amd64/kubectl

# Add the execute permissions to the file
chmod +x kubectl 

# Copy the binary to a folder in the PATH
mv kubectl /usr/local/bin

# Verify the Installation
kubectl version --client
```

## Install or update the latest version of the AWS CLI
```sh
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
# Reset the Old shell
exit
sudo su -
```

## To create a cluster You can create it by using eksctl, the AWS Management Console, or the AWS CLI

## Installing the eksctl

```sh
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo mv /tmp/eksctl /usr/local/bin
```

