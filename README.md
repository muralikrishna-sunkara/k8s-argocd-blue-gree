# k8s-argocd-blue-green

A sample project demonstrating **Blue-Green Deployment** strategy on Kubernetes using [ArgoCD](https://argoproj.github.io/argo-cd/). This repository provides manifests and instructions to implement zero-downtime deployments by leveraging ArgoCD's declarative GitOps approach.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Blue-Green Deployment Strategy](#blue-green-deployment-strategy)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This repository demonstrates how to perform Blue-Green deployments on a Kubernetes cluster with ArgoCD. Blue-Green deployment is a technique that reduces downtime and risk by running two identical production environments called Blue and Green.

You can use this project to learn, test, and bootstrap your own GitOps-based deployment workflows.

## Features

- Sample Kubernetes manifests for Blue-Green deployments
- ArgoCD Application definitions for managing deployments
- Step-by-step instructions for deployment and switching environments
- Zero-downtime application updates

## Prerequisites

- [Kubernetes](https://kubernetes.io/) cluster (local or cloud)
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started/) installed and configured
- `kubectl` CLI
- Git

## Getting Started

### 1. Clone this repository

```sh
git clone https://github.com/muralikrishna-sunkara/k8s-argocd-blue-gree.git
cd k8s-argocd-blue-gree
```

### 2. Install ArgoCD (if not already installed)

Follow the [official ArgoCD installation guide](https://argo-cd.readthedocs.io/en/stable/getting_started/).

### 3. Register Your Kubernetes Cluster with ArgoCD

Refer to the [ArgoCD documentation](https://argo-cd.readthedocs.io/en/stable/user-guide/cluster-bootstrapping/).

### 4. Deploy the Application

- Create an ArgoCD Application manifest referencing the blue environment.
- Sync the application via ArgoCD CLI or UI.

## Blue-Green Deployment Strategy

With Blue-Green deployments, you maintain two environments (Blue and Green). Only one of them serves live production traffic at a time. When a new version is ready, you deploy it to the idle environment and then switch the router (e.g., Service selector or Ingress rule) to point to the newly deployed version.

This strategy enables seamless rollbacks and minimizes downtime.

## Project Structure

```
k8s-argocd-blue-gree/
├── blue/
│   └── ...        # Kubernetes manifests for the Blue environment
├── green/
│   └── ...        # Kubernetes manifests for the Green environment
├── argocd/
│   └── ...        # ArgoCD Application/Project manifests
└── README.md
```

## Usage

1. Apply the blue environment manifests via ArgoCD.
2. Once ready to switch, apply the green environment manifests.
3. Update service selectors or ingress rules to point to the new environment.
4. Monitor for issues; if necessary, revert to the previous environment.

You can automate this switch with ArgoCD sync hooks or manual steps.

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License.
