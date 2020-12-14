Here I am going to log kOps pipeline

#### env:
1. $ `apt update && apt upgrade && apt install python3-pip`
1. $ `pip3 install pip --upgrade && pip3 install awscli`
1. $ `aws configure set aws_access_key_id "$AWS_ACCESS_KEY"`
1. $ `aws configure set aws_secret_access_key "$AWS_SECRET_KEY"`
1. $ `aws configure set default.region eu-central-1`
1. $ `aws iam get-user`
1. [install kops](https://kubernetes.io/docs/setup/production-environment/tools/kops/)
1. $ `kops completion bash >/etc/bash_completion.d/kops`
1. $ `aws s3api create-bucket --bucket ubuntu-on-bona-k8s-kops-store --region eu-central-1 --create-bucket-configuration LocationConstraint=eu-central-1`
1. $ `aws s3api put-bucket-versioning --bucket ubuntu-on-bona-k8s-kops-store --region eu-central-1 --versioning-configuration Status=Enabled`

export KOPS_STATE_STORE=s3://ubuntu-on-bona-k8s-kops-store
kops create cluster --name ubunut-on-bona.k8s.local --zones eu-central-1a --master-size t2.micro --node-size t2.micro --kubernetes-version 1.15.12
kops create secret --name ubunut-on-bona.k8s.local sshpublickey admin -i ~/.ssh/id_rsa.pub
