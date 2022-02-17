# demo-wordpress-iac 

## Project description

This repo contains IaC, based on Terraform, to manage AWS resources for my demo project at SoftServe DevOps Crash Course 2021. 

I use AWS EKS module for Terraform to deploy cluster. In my code I override and specify required and default values for the deployment, please, note that not all deployed resources are specified in the IaC code, i.e. policies and roles for master and worker nodes.

## Project pre-requisites

Jenkins with installed Docker, kubectl, Helm, AWS CLI, AWS Authenticator, Terraform. I used latest Jenkins Docker image and installed all required packages: https://hub.docker.com/r/jenkins/jenkins

## Project structure

versions.tf - describe backend and required providers

kubernetes.tf - kubernetes provider

variables.tf - declare variables

terraform.tfvars - specify variables

vpc.tf - create required network resources

security-groups.tf - create SGs for communication between worker nodes and master-worker nodes

eks-cluster.tf - specify worker nodes configurations

Jenkinsfile contains pipeline with the following stages: 
1. Terraform initialisation to get all required providers and modules.
2. And Terraform apply/delete to respectively create or destroy AWS infrastructure.

This pipeline is triggered by manual action through “Build with parameters”, where we chose whether we want to apply = create infrastructure, or delete = destroy it.
