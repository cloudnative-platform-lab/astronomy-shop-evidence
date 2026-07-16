# Astronomy Shop Cloud-Native Platform

We are Prasanna and Narendhiran, and we are building a cloud-native platform around the Astronomy Shop microservices application.

The purpose of this project is to demonstrate how a microservices application can be provisioned, built, deployed, operated and tested using AWS, Terraform, Amazon EKS, Kubernetes and GitOps practices.

This public repository documents the project through architecture diagrams, selected implementation details, sanitized command outputs, deployment results, operational tests, failures and improvements.

## Application overview

Astronomy Shop is a microservices-based e-commerce application containing the following nine services:

* frontend
* frontend-proxy
* product-catalog
* cart
* checkout
* payment
* currency
* recommendation
* image-provider

The `frontend-proxy` service acts as the main application entry point. The other application services communicate internally through Kubernetes networking.

## Platform scope

The project covers the following areas:

* AWS networking and infrastructure
* Terraform modules and environment configuration
* Amazon EKS and Kubernetes
* IAM, OIDC and workload access
* Amazon ECR and container-image delivery
* GitHub Actions CI/CD
* Helm and Argo CD GitOps
* Argo Rollouts
* AWS Load Balancer Controller
* runtime configuration
* HPA and Karpenter scaling
* Prometheus, Grafana, Loki and OpenTelemetry
* security controls
* backup and restoration
* failure testing and recovery
* cost management and FinOps
* technical troubleshooting

## Why this repository exists

A resume can list technologies such as AWS, Terraform, Kubernetes and Argo CD, but a list of tools does not show how those technologies were used or whether the person understands the decisions behind the implementation.

This repository connects each project claim to visible evidence.

As the project progresses, we will publish:

* architecture diagrams
* selected code excerpts
* sanitized command outputs
* AWS and Kubernetes deployment results
* CI/CD and GitOps evidence
* application traffic-flow validation
* scaling tests
* metrics, logs, traces and alerts
* failure and recovery tests
* backup and restore results
* security validation
* problems encountered and improvements made

## Public evidence and private implementation

The complete application, Terraform, CI/CD and GitOps implementations are maintained in private repositories because they contain reusable engineering work.

This public repository will provide enough evidence to explain:

* what we built
* why we selected the architecture
* how the components work together
* how the platform was deployed
* how the platform was tested
* what problems we encountered
* how those problems were resolved
* what tradeoffs and limitations remain

Selected implementation excerpts will be shared when they are required to support a technical claim.

The complete private repositories can also be demonstrated through a controlled live walkthrough during technical interviews.

## Contributors

### Prasanna

Prasanna’s main contribution areas are:

* AWS infrastructure
* Terraform
* Amazon EKS
* networking
* IAM and OIDC
* Amazon ECR
* ingress
* scaling infrastructure
* security controls
* backup and restoration
* cost management

### Narendhiran

Narendhiran’s main contribution areas are:

* GitHub Actions
* container-image delivery
* Helm
* Argo CD
* Argo Rollouts
* Kubernetes workloads
* runtime configuration
* Redis and Valkey integration
* observability
* troubleshooting

Both contributors review each other’s work through GitHub pull requests.

## Project progress

### Day 01 — Project introduction

**Status:** Published
**Contributors:** Prasanna and Narendhiran

We introduced the project, application scope, platform scope, contribution areas and the boundary between public evidence and private implementation.

[View the Day 01 project introduction](episodes/day-01-project-introduction.md)

### Day 02 — Architecture and traffic flow

**Status:** Next
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will explain the architecture, user traffic flow, AWS and Kubernetes boundaries, `frontend-proxy` routing, internal services and environment design.

Evidence link will be added after publication.

### Day 03 — Terraform and AWS foundation

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will cover the Terraform structure, AWS foundation, module dependencies and the separation between infrastructure bootstrap and platform configuration.

Evidence link will be added after publication.

### Day 04 — Amazon EKS, IAM and ECR

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will document the EKS cluster, IAM and OIDC integration, worker-node access and Amazon ECR repositories.

Evidence link will be added after publication.

### Day 05 — GitHub Actions CI/CD

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will explain how application code is built, tested, scanned, packaged as a container image and pushed to Amazon ECR.

Evidence link will be added after publication.

### Day 06 — Pipeline security

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will document container-image scanning, software bill of materials generation, signing and other pipeline security checks that are implemented.

Evidence link will be added after publication.

### Day 07 — Helm and GitOps structure

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will explain the Helm chart, environment-specific values and the GitOps repository structure.

Evidence link will be added after publication.

### Day 08 — Argo CD reconciliation

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will demonstrate how Argo CD detects changes in Git and reconciles the desired application state into Amazon EKS.

Evidence link will be added after publication.

### Day 09 — Argo Rollouts and rollback

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will document the application rollout strategy, deployment validation and rollback process.

Evidence link will be added after publication.

### Day 10 — ALB ingress and application traffic

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will demonstrate how public traffic reaches `frontend-proxy` through the Application Load Balancer and Kubernetes Ingress while backend services remain internal.

Evidence link will be added after publication.

### Day 11 — Runtime configuration and Valkey

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will explain application configuration, Kubernetes ConfigMaps and Secrets, service communication and the cart service’s Valkey dependency.

Evidence link will be added after publication.

### Day 12 — HPA and Karpenter scaling

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will demonstrate pod scaling through the Horizontal Pod Autoscaler and node scaling through Karpenter.

Evidence link will be added after publication.

### Day 13 — Observability

**Status:** Planned
**Main contributor:** Narendhiran
**Reviewer:** Prasanna

This episode will document metrics, dashboards, logs, traces and alerts using Prometheus, Grafana, Loki and OpenTelemetry.

Evidence link will be added after publication.

### Day 14 — Security, backup and cost management

**Status:** Planned
**Main contributor:** Prasanna
**Reviewer:** Narendhiran

This episode will document the security controls, backup and restore validation, operational safeguards and cost-management decisions used in the project.

Evidence link will be added after publication.

### Day 15 — Final validation and project summary

**Status:** Planned
**Contributors:** Prasanna and Narendhiran

This episode will bring together the completed evidence, test results, failures, improvements, remaining limitations and final project outcome.

Evidence link will be added after publication.

## Repository navigation

* [Day 01 — Project introduction](episodes/day-01-project-introduction.md)

New episode links will be added here after each pull request is reviewed and merged.

## Technical review

Feedback is welcome on the evidence published in this repository.

Useful review questions include:

* Does the evidence support the technical claim?
* Is an important dependency or risk missing?
* Is the design decision explained clearly?
* Is further validation required?
* Are the tradeoffs described honestly?
* Would the evidence be sufficient during a junior DevOps or Cloud Engineering interview?

Feedback can be shared through GitHub issues, pull-request comments or the related LinkedIn discussion.
