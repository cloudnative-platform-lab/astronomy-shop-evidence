# Astronomy Shop — Cloud Native Platform Engineering Portfolio

## Project Story Promise

Astronomy Shop tells the story of turning a distributed e-commerce application into an operable cloud platform.

The business scenario is simple: a customer must be able to browse astronomy products, view images and recommendations, add products to a cart, and complete checkout. The engineering challenge is not simple: the customer journey depends on multiple services, public edge routing, secure runtime configuration, managed data stores, release control, capacity management, and operational visibility.

This portfolio shows how Prasanna and Narendhiran designed the platform so that the same application journey can be provisioned, delivered, secured, observed, and operated through engineering controls rather than manual intervention.

**The promise:** every important platform claim leads to real evidence, and every future capability is clearly marked as planned rather than presented as complete.

## Portfolio Promise

This is an engineering portfolio, not a tutorial or a generic tool list. It shows what the Astronomy Shop platform is designed to do, how the architecture is organized, who built it, and where real environment evidence is stored.

Every completed capability is intended to be backed by screenshots, terminal output, dashboard views, Git history, or Terraform validation. Planned capability is labelled as planned; it is never presented as implemented.

## What Is Astronomy Shop?

Astronomy Shop is a cloud-native distributed e-commerce platform. Customers browse telescope products, view images and recommendations, add items to a cart, complete checkout and payment, then trigger email and shipping workflows.

The public Dev website is:
https://dev.astronomy-shop.store

The platform exists to demonstrate how a team can run that customer journey on AWS using repeatable infrastructure, Kubernetes-based microservices, automated delivery, managed data services, secure runtime identity, and operational controls.

## Information Promise to a Reviewer

Within a few minutes, this portfolio should make clear:

1. **What was built:** a distributed e-commerce platform with eleven Dev microservices on Amazon EKS.
2. **Why it was built:** to prove platform engineering practices beyond a manual container deployment.
3. **How it works:** customer traffic flows through the public edge into Kubernetes services and managed AWS dependencies.
4. **How it is delivered:** source code becomes immutable ECR images, GitOps desired state, and Argo CD-managed workloads.
5. **Who built it:** Prasanna and Narendhiran, collaborating across application, GitOps, and infrastructure lifecycles.
6. **What is proven:** detailed Dev evidence records validated implementation; Staging and Production remain future maturity stages until evidenced.

## Platform Goal

The platform is designed to provide:

- Automated AWS infrastructure provisioning.
- Automated application delivery from code change to healthy workload.
- Immutable container deployments through SHA256 image digests.
- Secure workload identity and runtime secret delivery.
- Kubernetes-native workload management and controlled releases.
- Elastic service and node capacity.
- Managed data dependencies instead of in-cluster databases.
- Public HTTPS delivery with edge protection.
- Operational visibility, cost controls, and evidence-based validation.

## Complete Platform Capability Map

The infrastructure repository contains a broader platform capability set than the current Dev deployment. This overview shows both the verified Dev implementation and the modules prepared for later environment maturity.

### Verified Dev Capabilities

Cloud foundation  
VPC, public/private subnets, route tables, NAT Gateway, security groups, KMS, S3

Kubernetes platform  
Amazon EKS, managed baseline nodes, EBS CSI driver, metrics-server, Karpenter, NodePool, NodeClaims, Dev namespace, NetworkPolicies

Application delivery  
GitHub Actions, private ECR, GitOps, Argo CD, ApplicationSet, Helm, Argo Rollouts, immutable image digests

Application runtime  
11 microservices, probes, HPA, ConfigMaps, External Secrets, OIDC, IRSA, PodDisruptionBudgets, graceful termination, Envoy proxy

Public edge  
Route 53-hosted public domain, ACM certificates, CloudFront, AWS WAF, ALB, Kubernetes Ingress, cert-manager, ExternalDNS, ALB access logs

Operations  
Prometheus, Grafana, kube-state-metrics, node exporter, AWS Budget, Terraform remote state, reusable Terraform modules, no-drift validation

Managed dependencies  
Redis/Valkey with TLS, Secrets Manager, application configuration, encrypted S3 application storage

### Terraform Capability Available but Disabled in Dev

Governance and audit  
CloudTrail, AWS Config, VPC Flow Logs, GuardDuty, Security Hub

Backup and recovery  
AWS Backup, cross-region disaster-recovery storage, Velero

Advanced Kubernetes security  
Kyverno, Falco, signed-image enforcement with Cosign policy

Persistent and application observability  
CloudWatch observability, Alertmanager, Loki, Tempo, OpenTelemetry Collector, persistent Prometheus and Grafana storage

Cost allocation  
Kubecost

Identity administration  
AWS IAM Identity Center / SSO permission-set and account-assignment wiring

Optional managed data  
RDS PostgreSQL deployment through the data-stores module

### Future Environment Capability

Staging  
Istio service-mesh traffic management, release rehearsal, failure testing, security testing, observability validation, performance testing

Production  
High availability, production approval gates, SLO monitoring, backup/recovery validation, disaster-recovery readiness, production-scale operational processes

**Status rule:** a module in Terraform represents an available platform capability; it becomes an implemented environment feature only after it is enabled, applied, and validated with evidence.

## Six Engineering Pillars

Astronomy Shop is organized against six practical platform engineering pillars.

### 1. Operational Excellence

Terraform, GitOps, Argo CD, Helm, Argo Rollouts, GitHub Actions, and reusable modules make infrastructure and application changes repeatable, reviewable, and recoverable through declared state.

### 2. Security

The design uses VPC segmentation, security groups, KMS encryption, private ECR, AWS Secrets Manager, External Secrets, EKS OIDC, IRSA, workload security contexts, NetworkPolicies, HTTPS, CloudFront, and AWS WAF.

### 3. Reliability

EKS workloads use probes, Argo Rollouts, PodDisruptionBudgets, graceful termination, Redis/Valkey, HPA, and Karpenter capacity provisioning. Dev proves the foundation; it does not claim production-scale reliability validation.

### 4. Performance and Scalability

CloudFront serves the public edge, HPA scales service replicas using CPU and memory, and Karpenter adds application-node capacity when workloads cannot be scheduled on existing nodes.

### 5. Cost Optimization

Dev uses controlled baseline capacity, elastic Karpenter capacity, a monthly AWS Budget, and intentionally avoids unnecessary Dev components such as Kubecost and persistent telemetry storage.

### 6. Sustainability and Resource Discipline

The environment favors right-sized Dev capacity, autoscaling, managed services, and clear lifecycle boundaries rather than permanently overprovisioned infrastructure. This is a design approach; no carbon-reduction claim is made without measurement.

## Portfolio Architecture

Customer  
→ Route 53 → CloudFront → AWS WAF → Application Load Balancer  
→ Kubernetes Ingress → frontend-proxy / Envoy → frontend and microservices  
→ Redis/Valkey and Amazon S3

Developer  
→ GitHub Actions → private Amazon ECR → immutable SHA256 digest  
→ GitOps repository → Argo CD → Helm → Argo Rollouts → EKS workload

Operators  
→ Terraform for infrastructure → Prometheus/Grafana for baseline visibility  
→ HPA and Karpenter for capacity → AWS Budget for Dev cost guardrails

## Three-Layer Repository Model

Application Repository  
→ service source code, Dockerfiles, GitHub Actions

GitOps Repository  
→ Helm chart, environment values, Argo CD applications, desired Kubernetes state

Infrastructure Repository  
→ Terraform modules, AWS resources, EKS platform, security, edge, operations

This separation keeps application code, cloud infrastructure, and Kubernetes deployment state independently reviewable while preserving one connected delivery flow.

## Environment Progression

DEV — verified now  
Integrated development validation at controlled cost.

STAGING — planned  
Production rehearsal with stronger validation, traffic management, failure testing, and performance testing.

PRODUCTION — planned  
Customer-facing operation with high availability, hardened controls, approvals, persistent operations data, and recovery readiness.

Only Dev is currently evidenced. Staging and Production are architectural goals, not completed claims.

## How to Review This Portfolio

1. Read [`01-Project-Overview`](01-Project-Overview/README.md) for the customer journey, runtime flow, delivery flow, and platform operation model.
2. Read [`02-Repository-Architecture`](02-Repository-Architecture/README.md) for contributors, ownership, and repository separation.
3. Read [`03-Environment-Validation`](03-Environment-Validation/README.md) for the linked Dev validation screenshots.

## Current Status

✅ Dev platform implementation and validation evidence are available.  
⏳ Staging and Production remain future implementation and evidence work.

## Evidence Repository Guide

```text
dev/
├── README.md
├── 01-Project-Overview/
├── 02-Repository-Architecture/
└── 03-Environment-Validation/
    ├── 1. Public Application & Networking/
    ├── 2. GitOps & Application Delivery/
    ├── 3. Kubernetes Platform & Runtime/
    ├── 4. Capacity & Scaling/
    ├── 5. Data & Security/
    ├── 6. Observability/
    ├── 7. Terraform/
    └── 8. FinOps/
```

Each validation area links directly to its screenshots from [`03-Environment-Validation`](03-Environment-Validation/README.md).

## Verification Summary

The Dev validation record confirms: all GitOps applications are healthy; all eleven application Pods are running; all Rollouts are available; HTTPS returns `200`; Prometheus/Grafana is deployed; an AWS Budget of USD 150 exists; and Terraform reports no drift.

## Result

✅ The Dev evidence repository is structured for fast technical review and real implementation verification.

## Known Limitations

All evidence must be sanitized. Never publish secret values, tokens, kubeconfig data, Terraform state, internal IP addresses, or unredacted AWS account details.
