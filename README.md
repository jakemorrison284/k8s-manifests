# k8s-manifests

Kubernetes manifests for all NovaPay services. This repository contains the configuration files needed to deploy and manage NovaPay's microservices on a Kubernetes cluster.

## Project Description
This repository provides declarative Kubernetes manifests for deploying NovaPay's core services, including payments and transaction processing engines. It helps streamline deployment, scaling, and management of services within Kubernetes environments.

## Prerequisites
Before using these manifests, ensure you have:
- A running Kubernetes cluster (version X.Y or later recommended)
- `kubectl` command-line tool installed and configured to access your cluster
- Appropriate permissions to create and manage resources on the cluster

## Installation Instructions
To get started with the Kubernetes manifests, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/jakemorrison284/k8s-manifests.git
   ```

2. Navigate to the project directory:
   ```bash
   cd k8s-manifests
   ```

## Directory Structure
- `payments-core/` - Manifests related to the payments core service
- `transaction-engine/` - Manifests for the transaction processing engine
- `redis-deployment.yaml` - Redis deployment manifest
- `RESOURCE_MANAGEMENT_GUIDELINES.md` - Guidelines for resource requests and limits
- `rollback-strategy.md` - Documentation on rollback procedures and strategies
- `project-documentation/` - Additional project-related documentation

## Usage
To apply the Kubernetes manifests, use the following command:
```bash
kubectl apply -f <manifest-file>.yaml
```
Replace `<manifest-file>` with the path to the manifest file or directory you want to apply.

### Examples
Apply all manifests in a directory:
```bash
kubectl apply -f payments-core/
```

Delete resources defined in a manifest:
```bash
kubectl delete -f redis-deployment.yaml
```

## Troubleshooting
- Ensure your `kubectl` context is set correctly to the desired cluster.
- Check resource quotas and limits if deployment fails.
- Refer to logs for pods that fail to start:
  ```bash
  kubectl logs <pod-name>
  ```
- See the [RESOURCE_MANAGEMENT_GUIDELINES.md](RESOURCE_MANAGEMENT_GUIDELINES.md) for best practices on resource allocation.

## Contributing
We welcome contributions! To contribute:

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
5. Create a pull request for review.

Please follow our coding and documentation standards and ensure all changes are tested.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support
For assistance, please open an issue on this repository or contact the maintainers.
