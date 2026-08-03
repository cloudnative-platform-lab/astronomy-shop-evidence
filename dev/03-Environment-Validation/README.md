# DEV Environment Validation

## Purpose

Validate the complete Astronomy Shop Dev delivery path from infrastructure provisioning to a running cloud-native application.

## Environment Difference

Dev prioritizes integration speed, fast feedback, and controlled cost. It is intentionally smaller and less operationally persistent than future Staging and Production environments.

## Evidence

### Public Application & Networking

- [Product browsing](<1. Public Application & Networking/01-products.png.png>)
- [Cart flow](<1. Public Application & Networking/01-public-applicationcart-flow.png.png>)
- [Checkout flow](<1. Public Application & Networking/01-public-applicationcheckout.png.png>)
- [Public application home page](<1. Public Application & Networking/01-public-applicationhomepage-products.png.png>)
- [ACM certificate](<1. Public Application & Networking/01-public-networkingacm-certificate.png.png>)
- [CloudFront distribution](<1. Public Application & Networking/01-public-networkingcloudfront.png.png>)
- [Route 53 record](<1. Public Application & Networking/01-public-networkingroute53.png.png>)
- [AWS WAF protection](<1. Public Application & Networking/01-public-networkingwaf.png.png>)

These screenshots verify that `https://dev.astronomy-shop.store` serves the customer journey through public DNS, CDN, WAF, TLS, ALB, Ingress, and frontend-proxy.

### GitOps & Application Delivery

- [Private ECR image](<2. GitOps & Application Delivery/03-gitops-deliveryecr-image.png.png>)
- [Argo CD application health](<2. GitOps & Application Delivery/gitops-deliveryargocd-health.png.png>)
- [GitHub Actions successful workflow](<2. GitOps & Application Delivery/gitops-deliverygithub-actions-success.png.png>)
- [Immutable image digest in GitOps](<2. GitOps & Application Delivery/gitops-deliveryimage-digest.png.png>)

These screenshots verify the delivery chain: CI builds an image, ECR stores it, GitOps records its immutable digest, and Argo CD reconciles it into Dev.

### Kubernetes Platform & Runtime

- [External Secrets synchronization](<3. Kubernetes Platform & Runtime/kubernetes-runtimeexternal-secrets.png.png>)
- [Horizontal Pod Autoscalers](<3. Kubernetes Platform & Runtime/kubernetes-runtimehpa.png.png>)
- [Running Dev Pods](<3. Kubernetes Platform & Runtime/kubernetes-runtimepods.png.png>)
- [Healthy Argo Rollouts](<3. Kubernetes Platform & Runtime/kubernetes-runtimerollouts.png.png>)

These screenshots verify that the Dev namespace receives secrets, runs the application workload, uses Rollouts for deployment state, and has HPA configuration.

### Capacity & Scaling

- [Karpenter NodeClaims](<4. Capacity & Scaling/capacitynodeclaims.png.png>)
- [Karpenter NodePool](<4. Capacity & Scaling/capacitynodepool.png.png>)
- [Ready cluster nodes](<4. Capacity & Scaling/capacitynodes.png.png>)

These screenshots verify that Karpenter has a ready NodePool and has provisioned application capacity through NodeClaims.

### Data & Security Integration

- [External Secret ready](<5. Data & Security/data-security external-secret-ready.png.png>)

This screenshot verifies runtime configuration is synchronized from the configured external secret source into Kubernetes.

### Observability

- [Grafana dashboard](<6. Observability/observabilitygrafana-dashboard.png.png>)
- [Prometheus `up` query](<6. Observability/observabilityprometheus-up.png.png>)

These screenshots verify that Grafana can query Prometheus and that the observed targets returned `up = 1` during validation.

### Infrastructure & Governance

- [Terraform no-drift plan](<7. Terraform/terraformterraform-plan.png.png>)
- [Bootstrap Dev Terraform outputs](<7. Terraform/01-bootstrap-dev-terraform-output.txt>)
- [Platform Dev Terraform outputs](<7. Terraform/02-platform-dev-terraform-output.txt>)
- [AWS Dev budget](<8. FinOps/finopsaws-budget.png.png>)

These artifacts verify the Bootstrap and Platform Terraform states, the no-drift validation result, and the Dev monthly cost budget.

## Verification

The evidence verifies the Dev lifecycle from public access through CI/CD, GitOps, Kubernetes runtime, scaling, observability, Terraform reconciliation, and FinOps control.

## Result

Dev environment validation evidence is linked to the actual screenshots captured from the implemented platform.

## Dev Boundaries

- Low-cost worker capacity is used for Dev validation; node-exporter coverage is partial where node pod capacity is exhausted.
- No production SLA, production-scale load validation, persistent logs/traces, Alertmanager paging, or persistent Prometheus/Grafana storage is claimed.
- No production approval gates, production-scale resilience exercises, or completed disaster-recovery exercises are claimed.
