# k8s-manifests

Kubernetes manifests for all NovaPay services.

## Project Overview
This repository contains Kubernetes manifests that define the deployment, service, and configuration resources for all NovaPay services. The manifests are designed to facilitate the deployment and management of NovaPay applications within Kubernetes clusters, ensuring consistency, scalability, and ease of maintenance.

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
