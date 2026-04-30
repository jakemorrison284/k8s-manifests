# Documentation for virtual-service.yaml

## Overview
The `virtual-service.yaml` file defines how requests to the `payments-core` service are routed within the Istio service mesh. This configuration is crucial for managing API traffic and ensuring proper communication between services.

## Detailed Breakdown

- **apiVersion**: 
  - `networking.istio.io/v1alpha3`: This specifies the API version of the Istio networking configuration.

- **kind**: 
  - `VirtualService`: This indicates that the object being defined is a Virtual Service.

- **metadata**: 
  - **name**: 
    - `payments-core`: The name of the Virtual Service.
  - **namespace**: 
    - `novapay`: The Kubernetes namespace in which this Virtual Service is defined.

- **spec**: 
  - **hosts**:
    - `novapay/payments-core`: This specifies the host for which this Virtual Service is responsible. It indicates that traffic directed to this host will be managed according to the routing rules defined below.
  
  - **http**:
    - This section defines the HTTP routing rules.
    - **route**: 
      - Contains a list of routing rules.
      - **destination**:
        - **host**: `novapay/payments-core`: Specifies the service to which traffic will be routed.
        - **port**:
          - **number**: `8080`: The port on which the `payments-core` service is listening.
      - **weight**: `100`: Indicates the weight for routing traffic to this destination.