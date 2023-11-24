#command to create EKS cluster

eksctl create cluster --name demo-cluster --region us-east-1 --fargate

#Command to download the kubeconfig file

aws eks update-kubeconfig --name demo-cluster --region us-east-1

#command to delete EKS cluster

eksctl delete cluster --name demo-cluster --region us-east-1

#REFER this GITHUB repo

https://github.com/iam-veeramalla/aws-devops-zero-to-hero/tree/main/day-22
