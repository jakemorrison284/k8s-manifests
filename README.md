# k8s-manifests

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)  
[![Build Status](https://img.shields.io/badge/build-pending-lightgrey.svg)](#)  
[![Latest Release](https://img.shields.io/badge/release-v1.0-blue.svg)](#)

Kubernetes manifests for all NovaPay services.

## Project Overview
This repository contains Kubernetes manifests that define the deployment, service, and configuration resources for all NovaPay services. The manifests are designed to facilitate the deployment and management of NovaPay applications within Kubernetes clusters, ensuring consistency, scalability, and ease of maintenance.

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

## Key Manifests
- `redis-deployment.yaml`: Deployment configuration for Redis cache service.
- Manifests in `payments-core/`: Kubernetes resources for the Payments Core service.
- Manifests in `transaction-engine/`: Kubernetes resources for the Transaction Engine service.

## Troubleshooting
- Ensure your kubectl context is set to the correct cluster.
- Check for resource conflicts or missing permissions.
- Review pod and event logs for error messages.

## Additional Resources
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [NovaPay Documentation](https://docs.novapay.com) (replace with actual URL if available)

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
