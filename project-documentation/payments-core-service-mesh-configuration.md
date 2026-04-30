# payments-core Service Mesh Configuration

This document provides the configuration details for securing and enhancing the resilience of the payments-core service within the Istio service mesh. Proper service mesh configuration is critical for ensuring secure communication, fault tolerance, and overall reliability.

Note: These configurations apply to the `novapay` namespace.

## PeerAuthentication (Strict mTLS Enforcement)

The following PeerAuthentication resource enforces strict mutual TLS (mTLS) for the payments-core service, ensuring that all traffic between services is encrypted and authenticated.

```yaml
apiVersion: security.istio.io/v1beta1
kind: PeerAuthentication
metadata:
  name: payments-core-strict-mtls
  namespace: novapay
spec:
  selector:
    matchLabels:
      app: payments-core
  mtls:
    mode: STRICT
```

- `mode: STRICT` mandates that only mTLS traffic is allowed, rejecting any plaintext communication.

## DestinationRule (Circuit Breaking and mTLS)

The DestinationRule configures circuit breaking policies along with mTLS settings for the payments-core service to improve fault tolerance and secure communication.

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: DestinationRule
metadata:
  name: payments-core-cb
  namespace: novapay
spec:
  host: novapay/payments-core
  trafficPolicy:
    tls:
      mode: ISTIO_MUTUAL  # Enable mTLS
    connectionPool:
      tcp:
        maxConnections: 100
      http:
        http1MaxPendingRequests: 50
        maxRequestsPerConnection: 100
    outlierDetection:
      consecutiveErrors: 5
      interval: 10s
      baseEjectionTime: 30s
      maxEjectionPercent: 50
```

- `tls.mode: ISTIO_MUTUAL` enables automatic mutual TLS between client and server.
- `connectionPool` settings limit the number of connections and requests to prevent overload.
- `outlierDetection` settings automatically eject unhealthy hosts from the load balancing pool based on error rates.

## Applying the Configuration

To apply or update these configurations, use:

```bash
kubectl apply -f payments-core-peer-authentication.yaml
kubectl apply -f payments-core-destination-rule.yaml
```

Replace the file names with the actual paths to your YAML manifests.

## Summary

This configuration ensures that the payments-core service communicates securely using mTLS, and improves resilience through circuit breaking and outlier detection policies, resulting in a more reliable and secure service mesh environment.
