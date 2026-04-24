## ArgoCD Repository

This project implements a full CI/CD and GitOps pipeline using Terraform, Ansible, GitLab CI, Docker and ArgoCD.

The applications and configurations in this repo are linked to our Infrastructure as Code (IaC) repository, which is managed using Terraform.

All infrastructure is provisioned and maintained via Terraform, while this repository is responsible for deploying and synchronizing applications in Kubernetes through ArgoCD.

In short:

- IaC repo (Terraform) → provisions and manages infrastructure  
- ArgoCD repo → handles application deployment on top of the infrastructure  

