### Jenkins server setup with Helm to deploy into Kubernetes cluster

## Download and Install helm 
```sh
su - jenkins
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## Test with helm command
```sh
helm version
helm list
# Not able to connect Jenkins server with the k8s cluster
```
## Copy config file from EKS Management host to Jenkins home directory at .kube/config
```sh
mkdir /var/lib/jenkins/.kube
copy config file under .kube directory with jenkins ownership
```

## Try again 
```sh
helm list
chmod 600 /var/lib/jenkins/.kube/config
```

## Add a Stable repo to Helm
```sh
helm repo add stable https://charts.helm.sh/stable
# Display all the helm charts within the stable repo
helm search repo stable
```

## Pull Helm Chart from stable repo modify it and create a new package
```sh
# Search for mysql helm chart
helm search repo stable/mysql
# Download the chart locally to made some changes
helm install repo stable/mysql
helm pull stable/mysql # as a package
tar -xzvf mysql-1.6.9.tgz
## all the yaml files are within mysql/templates
## after made the changes update the version inside the Chart.yaml
```

## Deploy the helm chart again
```sh
helm package mysql 
```

### Deploy the helm chart into the cluster
```sh
helm install mydb  mysql-1.6.9.tgz # is already exist on my local other wise
helm install mydb stable/mysql
```
