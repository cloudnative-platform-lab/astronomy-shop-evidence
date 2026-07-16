# Astronomy Shop Cloud-Native Platform

This repository contains the public technical evidence for the Astronomy Shop cloud-native platform project developed by Prasanna and Narendhiran.

The project uses the Astronomy Shop microservices application as a realistic workload for demonstrating how cloud infrastructure, container delivery, Kubernetes, GitOps, observability, security, backup, scaling and cost controls work together on AWS.

Our objective is not simply to deploy an application to Amazon EKS. We are documenting how the platform was designed, implemented, tested, debugged and improved.

## Application overview

The Astronomy Shop application contains nine microservices:

- frontend
- frontend-proxy
- product-catalog
- cart
- checkout
- payment
- currency
- recommendation
- image-provider

The `frontend-proxy` service acts as the main application entry point. The remaining services communicate internally through Kubernetes networking.

This application gives us a realistic environment for validating application delivery, service communication, scaling, monitoring, failure recovery and platform operations.

## Platform scope

The project covers the following areas:

- AWS networking and infrastructure
- Terraform modules and environment configuration
- Amazon EKS and Kubernetes
- IAM, OIDC and workload permissions
- Amazon ECR and container-image management
- GitHub Actions CI/CD
- Helm-based application packaging
- Argo CD GitOps reconciliation
- Argo Rollouts and controlled deployments
- AWS Load Balancer Controller and ALB ingress
- Kubernetes runtime configuration
- HPA and Karpenter scaling
- Prometheus and Grafana monitoring
- Loki logging
- OpenTelemetry metrics, logs and traces
- security controls
- backup and restore
- cost awareness and FinOps
- troubleshooting and debugging
- platform limitations and technical tradeoffs

## Repository model

The project is maintained under the `cloudnative-platform-lab` GitHub organization.

It is divided into four repositories:

### `astronomy-shop-evidence` — Public

This repository contains the public documentation and technical evidence for the project.

It includes architecture explanations, selected implementation excerpts, command outputs, deployment results, testing evidence, failures, fixes, limitations and improvements.

### `astronomy-shop-app` — Private

This repository contains the application source code, Dockerfiles, service configuration and application-level CI workflows.

### `astronomy-shop-infrastructure` — Private

This repository contains the Terraform modules, AWS infrastructure configuration, Amazon EKS setup, networking, IAM, security, backup, observability and platform configuration.

### `astronomy-shop-gitops` — Private

This repository contains the Helm charts, environment values, Argo CD applications, Kubernetes manifests, Argo Rollouts configuration and GitOps deployment structure.

## Why the implementation repositories are private

The complete Terraform modules, CI/CD workflows and GitOps configuration required significant time to design, test, troubleshoot and improve.

Publishing the full repositories would allow the implementation to be copied, reused as a ready-made project or presented by someone else as their own work.

For that reason, the complete implementation remains private.

Keeping the repositories private does not mean that the project depends on unsupported claims. Every major technical claim will be connected to visible evidence in this public repository.

The private repositories can also be demonstrated through a controlled live walkthrough during technical interviews.

## How the project will be proven

The evidence published in this repository may include:

- architecture diagrams
- selected and sanitized code excerpts
- Terraform validation results
- sanitized Terraform plan summaries
- GitHub pull requests and review history
- GitHub Actions workflow results
- Amazon ECR image information
- Kubernetes command outputs
- Argo CD synchronization results
- deployment screenshots
- running workload information
- scaling tests
- failure and recovery tests
- backup and restore results
- monitoring dashboards
- logs and traces
- security validation
- problems encountered and improvements made

A screenshot alone will not be treated as complete proof when stronger evidence is available.

For example, a CI/CD claim may be supported through a workflow excerpt, a successful pipeline run, an image published to Amazon ECR, a GitOps image-tag update, an Argo CD synchronization result and the Kubernetes workload running the new image.

A Terraform claim may be supported through a selected configuration excerpt, a successful `terraform validate` result, a sanitized plan summary and the corresponding AWS resource.

The purpose is to demonstrate the implementation, the result and the technical understanding without publishing the complete reusable source.

## Information that will not be published

The public evidence will not expose:

- AWS access keys
- GitHub tokens
- passwords
- Kubernetes secrets
- `.env` files
- Terraform state files
- kubeconfig files
- private certificates
- sensitive backend configuration
- unnecessary AWS account identifiers
- complete reusable Terraform modules
- complete private GitOps values
- private repository credentials

All evidence will be reviewed and sanitized before publication.

## Collaboration model

Prasanna and Narendhiran work through their individual GitHub accounts.

Each topic has a primary contributor, but both contributors review and understand the complete platform.

The normal workflow is:

1. The primary contributor creates a branch.
2. The contributor prepares the implementation evidence and documentation.
3. The other contributor reviews the pull request.
4. Any requested changes are completed.
5. The pull request is approved and merged.
6. The public evidence is published only after the GitHub update is complete.

This process creates a verifiable record of contribution, review and collaboration.

## Primary focus areas

### Prasanna

Prasanna’s primary focus areas include:

- AWS architecture
- Terraform structure
- Amazon EKS foundation
- networking
- IAM and OIDC
- Amazon ECR
- ingress and load balancing
- scaling infrastructure
- security controls
- backup planning
- FinOps and cost awareness
- platform limitations and tradeoffs

### Narendhiran

Narendhiran’s primary focus areas include:

- GitHub Actions CI/CD
- Docker image delivery
- Helm configuration
- Argo CD
- GitOps deployment flow
- Argo Rollouts
- Kubernetes workloads
- runtime configuration
- Redis and Valkey integration
- observability
- troubleshooting and debugging

These focus areas describe how the work is organized. They do not limit either contributor’s understanding of the complete platform.

## Current progress

### Day 01 — Project introduction

The project objective, application scope, platform scope, contributor focus areas, repository model and public-evidence approach have been documented.

[Read the Day 01 project introduction](episodes/day-01-project-introduction.md)

## 15-day evidence series

The project will be documented through the following evidence topics:

1. **Project introduction** — Project scope, repository model, contributor focus areas and evidence approach.
2. **Architecture and traffic flow** — Platform architecture, AWS boundaries, Kubernetes boundaries and end-to-end request flow.
3. **Terraform and AWS foundation** — Terraform structure, networking, environment configuration and infrastructure validation.
4. **Amazon EKS, IAM and Amazon ECR** — Cluster foundation, workload permissions and image-storage design.
5. **GitHub Actions CI/CD** — Application build, test, container-image creation and image publishing.
6. **Pipeline security** — OIDC authentication, permissions, image scanning and secure delivery controls.
7. **Helm and GitOps structure** — Helm charts, environment values and GitOps repository organization.
8. **Argo CD reconciliation** — Desired-state synchronization, drift detection and deployment verification.
9. **Argo Rollouts and rollback** — Controlled releases, rollout validation and rollback behaviour.
10. **ALB ingress and application traffic** — External traffic, ingress configuration and service routing.
11. **Runtime configuration and Valkey** — Application configuration, Kubernetes runtime settings and data-service integration.
12. **HPA and Karpenter scaling** — Pod scaling, node provisioning and workload response under load.
13. **Observability** — Metrics, logs, traces, dashboards and alerting.
14. **Security, backup and cost management** — Security validation, backup planning, restore testing and FinOps controls.
15. **Final validation and project summary** — Complete evidence review, remaining limitations and final project assessment.

Each topic will be marked as published only after the related GitHub pull request has been reviewed and merged.

## Repository structure

The repository begins with the project README and the Day 1 introduction:

astronomy-shop-evidence/
├── README.md
└── episodes/
    └── day-01-project-introduction.md