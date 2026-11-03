# SparrowX Labs

SparrowX Labs is a platform engineering project for building and operating Kubernetes services through GitOps, reusable delivery workflows, Crossplane infrastructure, and developer self-service automation.

The project demonstrates how a platform team can provide golden paths for application teams while keeping infrastructure and application state declarative, reviewable, and auditable.

## Platform overview

The platform runs development and production workloads in separate namespaces on the same Kubernetes cluster. Argo CD reconciles applications from Git, while Crossplane provisions cloud resources through compositions, XRDs, XRs, and providers.

The target developer experience is a self-service automation control plane installed with Helm. Platform teams define templates and workflows as Kubernetes CRs; developers discover the workflows available to their teams, fill in validated forms, run them, and inspect the resulting pull requests, applications, infrastructure resources, and history.

## Repositories

| Repository | Purpose |
| --- | --- |
| [`project-overview`](https://github.com/SparrowX-Labs/project-overview) | Architecture, GitOps, build-once-promote-many, Crossplane, Argo CD, Backstage, and platform documentation |
| [`terraform`](https://github.com/SparrowX-Labs/terraform) | Foundational AWS infrastructure and cluster provisioning |
| [`crossplane`](https://github.com/SparrowX-Labs/crossplane) | Crossplane providers, XRDs, compositions, and infrastructure abstractions |
| [`ArgoCD-Apps`](https://github.com/SparrowX-Labs/ArgoCD-Apps) | Argo CD applications and environment declarations |
| [`EKS-HelmCharts`](https://github.com/SparrowX-Labs/EKS-HelmCharts) | Helm charts for platform and application deployments |
| [`Custom-Apps-HelmCharts`](https://github.com/SparrowX-Labs/Custom-Apps-HelmCharts) | Application-specific Helm charts and deployment configuration |
| [`workflows-templates`](https://github.com/SparrowX-Labs/workflows-templates) | Reusable GitHub Actions workflows for testing, security, image delivery, promotion, and deployment |
| [`gateway-api`](https://github.com/SparrowX-Labs/gateway-api) | API gateway and service routing configuration |
| [`customer-api`](https://github.com/SparrowX-Labs/customer-api) | Customer management service |
| [`notification-api`](https://github.com/SparrowX-Labs/notification-api) | Notification service |
| [`task-api`](https://github.com/SparrowX-Labs/task-api) | Task management service |
| [`billing-api`](https://github.com/SparrowX-Labs/billing-api) | Billing service |
| [`reporting-api`](https://github.com/SparrowX-Labs/reporting-api) | Reporting service |
| [`web-portal`](https://github.com/SparrowX-Labs/web-portal) | Web frontend |
| [`backstage`](https://github.com/SparrowX-Labs/backstage) | Developer portal and service catalog reference implementation |
| [`backstage-pyactions`](https://github.com/SparrowX-Labs/backstage-pyactions) | Python automation layer used by the earlier Backstage self-service implementation |

## GitOps delivery model

Application and infrastructure changes are promoted through Git. Reusable workflows standardize testing, security checks, image creation, deployment, and promotion across application repositories.

The delivery model follows **Build Once, Promote Many**:

1. Pull requests run tests, security checks, and validation.
2. A merge creates one immutable, signed image artifact.
3. Development deploys and validates that exact artifact.
4. Production promotes the already-tested artifact rather than rebuilding it.

Terraform, Helm, Crossplane, Argo CD, and application repositories have separate responsibilities and repository-level configuration. Shared organization variables and secrets are used where appropriate, while infrastructure repositories retain their own repository-specific configuration.

## Self-service automation direction

The long-term direction is a Kubernetes-native self-service automation control plane rather than a Backstage-dependent implementation.

The planned product will provide:

- a Helm chart that installs the backend, frontend, CRDs, RBAC, service account, and PostgreSQL integration;
- workflow and template CRs for platform-team-owned golden paths;
- team-aware workflow visibility and user/team-scoped execution history;
- administrator-only detailed logs and audit records;
- GitHub and GitLab provider integrations;
- Argo CD and Crossplane integrations;
- AWS, Azure, and GCP workload identity support;
- event-driven notifications through a separate worker for successful and failed workflows.

The control plane coordinates existing platform systems. It does not replace Git providers, Kubernetes, Argo CD, Crossplane, cloud providers, or durable workflow engines.

## Explore the project

- [Project overview](https://github.com/SparrowX-Labs/project-overview)
- [Build Once, Promote Many](https://github.com/SparrowX-Labs/project-overview/blob/main/build-once-promote-many.md)
- [Crossplane, Argo CD, and infrastructure provisioning](https://github.com/SparrowX-Labs/project-overview/blob/main/crossplane-and-argocd.md)
- [Backstage self-service automation](https://github.com/SparrowX-Labs/project-overview/blob/main/backstage.md)
- [Workflow templates](https://github.com/SparrowX-Labs/workflows-templates)

> SparrowX Labs is a platform engineering portfolio project focused on repeatable Kubernetes delivery, GitOps infrastructure, and developer self-service automation.
