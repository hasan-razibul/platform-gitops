# Platform GitOps

This repository contains the desired state for applications deployed by the
AI-Native Internal Developer Platform.

The repository is consumed by Argo CD.

## Repository Structure

```text
platform-gitops/
│
├── applications/
│   └── <application>/
│
└── environments/
    ├── dev/
    ├── staging/
    └── production/
```

## Responsibilities

This repository contains:

- Application deployment configuration
- Helm values
- Environment-specific configuration
- Kubernetes manifests
- Argo CD application definitions

The platform implementation itself is maintained in the
`ai-native-platform` repository.

## Deployment Model

```text
GitHub
   |
   v
GitOps Repository
   |
   v
Argo CD
   |
   v
Kubernetes
```

Argo CD continuously reconciles the Kubernetes cluster against the desired
state stored in this repository.

## Environments

### Development

Used for local and development workloads.

### Staging

Used for pre-production validation.

### Production

Used for production workloads.

## GitOps Principles

Changes to application deployments should be made through Git.

Direct changes to Kubernetes using `kubectl` should be avoided except for
debugging and emergency operations.

All production changes should be:

- Version controlled
- Reviewable
- Auditable
- Reversible