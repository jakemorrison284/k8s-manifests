# payments-core Service Mesh Configuration

## PeerAuthentication (Strict mTLS)

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

## DestinationRule (Circuit Breaking and mTLS)

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

This configuration aims to provide secure, reliable, and resilient communication for the payments-core service within the Istio service mesh.
