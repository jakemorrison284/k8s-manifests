# k8s-manifests

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)  
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/jakemorrison284/k8s-manifests/actions)  
[![Latest Release](https://img.shields.io/badge/release-v1.0-blue.svg)](https://github.com/jakemorrison284/k8s-manifests/releases/latest)

<!-- Additional badges can be added here, e.g., coverage, linting, security scans -->

Kubernetes manifests for all NovaPay services.

## Table of Contents
- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Installation Instructions](#installation-instructions)
- [Usage](#usage)
  - [Additional Usage Examples](#additional-usage-examples)
  - [Managing Updates](#managing-updates)
- [Quick Start](#quick-start)
- [Key Manifests](#key-manifests)
- [Rollback Strategy](#rollback-strategy)
- [Environment and Configuration](#environment-and-configuration)
- [Known Issues](#known-issues)
- [Troubleshooting](#troubleshooting)
- [Additional Resources](#additional-resources)
- [Contact and Support](#contact-and-support)
- [Contributing](#contributing)
- [License](#license)

## Project Overview
This repository contains Kubernetes manifests that define the deployment, service, and configuration resources for all NovaPay services. The manifests are designed to facilitate the deployment and management of NovaPay applications within Kubernetes clusters, ensuring consistency, scalability, and ease of maintenance.

### Key Services Overview
- **Redis Cache Service:** Provides a high-performance caching layer to improve application response times and reduce database load.
- **Payments Core Service:** The central service responsible for processing and managing payment transactions securely.
- **Transaction Engine Service:** Handles transaction workflows, business logic, and integrates with external payment gateways.

## Prerequisites
- Kubernetes cluster (version 1.20 or higher recommended)
- kubectl command-line tool installed and configured to access your cluster
- Appropriate cluster access permissions to create and manage resources

## Installation Instructions
To set up the Kubernetes manifests, follow these steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/jakemorrison284/k8s-manifests.git
   ```
2. Navigate to the project directory:
   ```bash
   cd k8s-manifests
   ```

### Dependencies
- Ensure you have `kubectl` installed.
- If using Helm or Kustomize for deployment customization, please install and configure them accordingly.

## Usage
To apply the Kubernetes manifests, use the following command:
```bash
kubectl apply -f <manifest-file>.yaml
```
Replace `<manifest-file>` with the name of the manifest file you want to apply.

Alternatively, to deploy all manifests in the repository, run:
```bash
kubectl apply -f .
```

### Additional Usage Examples
- Deploy only the Redis service:
  ```bash
  kubectl apply -f redis-deployment.yaml
  ```
- Deploy the Payments Core service:
  ```bash
  kubectl apply -f payments-core/
  ```
- Deploy the Transaction Engine service:
  ```bash
  kubectl apply -f transaction-engine/
  ```

**Note:** These manifests assume you are using the default Kubernetes namespace. Specify the namespace with the `-n <namespace>` flag if necessary. Ensure your `kubectl` context is set to the target cluster.

### Managing Updates
When updating manifests, use the `kubectl apply` command again to apply changes without downtime. For rolling updates, consider Kubernetes deployment strategies such as rolling update or blue-green deployments.

## Quick Start
For a minimal deployment to get started quickly, run:
```bash
kubectl apply -f redis-deployment.yaml
kubectl apply -f payments-core/
kubectl apply -f transaction-engine/
```
This will deploy the core services required for basic operation.

## Key Manifests
- [`redis-deployment.yaml`](https://github.com/jakemorrison284/k8s-manifests/blob/main/redis-deployment.yaml): Deployment configuration for Redis cache service.
- Manifests in [`payments-core/`](https://github.com/jakemorrison284/k8s-manifests/tree/main/payments-core/): Kubernetes resources for the Payments Core service.
- Manifests in [`transaction-engine/`](https://github.com/jakemorrison284/k8s-manifests/tree/main/transaction-engine/): Kubernetes resources for the Transaction Engine service.

## Rollback Strategy
For rollback procedures, please refer to the [rollback-strategy.md](rollback-strategy.md) file. It outlines steps to revert deployments safely and minimize downtime.

## Environment and Configuration
Some manifests may require configuration through environment variables, ConfigMaps, or Secrets. Please review individual manifests for specific configuration requirements. Ensure sensitive data is managed securely using Kubernetes Secrets.

## Known Issues
- Currently, there are no major known issues. Please check the issue tracker for any updates.
- If you encounter unexpected behavior, please report it via the repository issues.

## Troubleshooting
- Ensure your kubectl context is set to the correct cluster.
- Check for resource conflicts or missing permissions.
- Review pod and event logs for error messages.
- Common Errors:
  - `Error from server (AlreadyExists)`: Resource already exists. Consider deleting the existing resource or updating it.
  - `Error from server (Forbidden)`: Insufficient permissions. Verify your RBAC settings.
  - `CrashLoopBackOff` status: Check container logs for application errors or misconfigurations.
- Additional Resources for Troubleshooting:
  - [Kubernetes Troubleshooting Guide](https://kubernetes.io/docs/tasks/debug/)
  - [Common Kubernetes Error Messages](https://kubernetes.io/docs/concepts/cluster-administration/troubleshooting/)

## Additional Resources
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [NovaPay Documentation](https://docs.novapay.com) <!-- Please replace with the actual URL if available -->

## Contact and Support
For support or questions, please contact the NovaPay DevOps team at [devops@novapay.com](mailto:devops@novapay.com).

## Contributing
We welcome contributions! If you'd like to contribute to this repository, please follow these steps:
1. Fork the repository.
2. Create a new branch for your feature or bug fix:
   ```bash
   git checkout -b my-feature-branch
   ```
3. Make your changes and commit them:
   ```bash
   git commit -m "Add some feature"
   ```
4. Push to the branch:
   ```bash
   git push origin my-feature-branch
   ```
5. Create a pull request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
