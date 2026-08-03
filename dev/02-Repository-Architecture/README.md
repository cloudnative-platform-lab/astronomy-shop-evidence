# 02 — Repository Architecture and Ownership

## Purpose
Show how the project is owned and maintained as a platform, with separate lifecycles for application code, Kubernetes desired state, and AWS infrastructure.

## Contributors
**Prasanna** and **Narendhiran** collaborated on Astronomy Shop.

Two engineers were appropriate for this project because the platform spans several interdependent engineering domains: AWS infrastructure, Terraform automation, EKS, CI/CD, GitOps, security and identity, managed data services, scaling, observability, and operational validation.

The collaboration produced one architecture, while allowing work and review to be divided by platform area rather than treating the project as a single application deployment.

## Repository Ownership Tree

Astronomy Shop Platform
│
├── Application Repository
│   ├── 11 microservices source code
│   ├── GitHub Actions CI workflows
│   ├── Dockerfiles and runtime entry points
│   └── Container image build definitions
│
├── GitOps Repository
│   ├── Reusable Helm chart
│   ├── Per-service Dev values
│   ├── Argo CD root Application
│   ├── ApplicationSet definitions
│   ├── Rollout, Service, HPA, policy, and configuration templates
│   └── Immutable ECR image digest references
│
└── Infrastructure Repository
    ├── Terraform bootstrap and platform stacks
    ├── Reusable Terraform modules
    ├── VPC, EKS, managed data, KMS, and S3 resources
    ├── Edge, DNS, certificate, WAF, and ingress resources
    ├── IAM, OIDC, IRSA, secrets, and security configuration
    └── Karpenter, observability, and FinOps configuration


## Lifecycle Model
Application repository
→ changes source code and container build logic

Infrastructure repository
→ changes AWS, EKS, identity, networking, and platform capabilities

GitOps repository
→ declares the exact immutable image and Kubernetes desired state
→ Argo CD reconciles that state into the cluster

## Why the Repositories Are Separate
- **Application lifecycle separation:** service code can change without editing Terraform.
- **Infrastructure lifecycle separation:** cloud changes are planned and applied through Terraform without directly editing application manifests.
- **GitOps source of truth:** the GitOps repository records exactly which image digest and configuration should run in Dev.
- **Reviewable ownership:** a release, a cloud change, and a Helm/GitOps change can be reviewed independently while remaining connected through the delivery flow.
- **Private implementation protection:** source code, Terraform state, credentials, and internal values remain private; only sanitized evidence is published.

## Evidence and Result
GitHub Actions history, ECR digest references, GitOps commits, Argo CD application status, Helm values, and Terraform module structure provide the implementation record.

✅ Repository separation makes the platform repeatable, reviewable, and maintainable across its different engineering lifecycles.

## Current Scope Boundary
Public evidence explains ownership and validation. It does not expose private source code, secret values, Terraform state, kubeconfig data, or internal endpoints.
