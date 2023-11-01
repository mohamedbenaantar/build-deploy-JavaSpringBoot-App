## Create an IAM Role and attache it to EC2 instance Management Host 

## Create EKS cluster and nodes from EC2 Management Host
```sh
eksctl create cluster --name cluster-name  \
--region region-name \
--node-type instance-type \
--nodes-min 2 \
--nodes-max 2 \ 
--zones <AZ-1>,<AZ-2>
```
## Example 
```sh
eksctl create cluster --name cluster-01 \
   --region us-east-1 \
--node-type t2.medium \
```

## To delete the EKS clsuter
```sh
eksctl delete cluster cluster-01 --region us-east-1 --zones us-east-1a,us-east-1b,us-east-1c,us-east-1d
```

## Validate the cluster using by checking nodes and by creating a pod
```sh
kubectl get nodes
kubectl run pod tomcat --image=tomcat 
```