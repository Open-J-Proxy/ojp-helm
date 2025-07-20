# OJP Server Helm Chart

Deploy OJP Server using `ojp/ojp-server` Helm Charts.

## Usage
Install OJP Server
```console
# Add the OJP Helm repository
helm repo add ojp https://ojp.github.io/ojp-helm

# Update the Helm repository
helm repo update

# Install the OJP Server chart
helm install ojp-server ojp/ojp-server \
    --namespace=ojp --create-namespace
```

Uninstall OJP Server
```console
helm uninstall ojp-server --namespace ojp
```

<!-- server:
  port: 1059
  prometheusPort: 9090
  threadPoolSize: 200
  circuitBreakerTimeout: "60000"
  allowedIps: "0.0.0.0/0"
  prometheusAllowedIps: "0.0.0.0/0"
  opentelemetry:
    enabled: true
  logLevel: INFO -->

### App parameters
| Name                       | Description                                    | Value                  |
| -------------------------- | ---------------------------------------------- | ---------------------- |
| `server.port`            | OJP Server Port                               | `1059`                 |
| `server.prometheusPort`  | OJP Server Prometheus Port                    | `9090`                 |
| `server.threadPoolSize`  | OJP Server Thread Pool Size                   | `200`                  |
| `server.circuitBreakerTimeout` | OJP Server Circuit Breaker Timeout | `60000`               |
| `server.allowedIps`       | OJP Server Allowed IPs                        | `0.0.0.0/0`           |
| `server.prometheusAllowedIps` | OJP Server Prometheus Allowed IPs | `0.0.0.0/0`           |
| `server.opentelemetry.enabled` | OJP Server OpenTelemetry Enabled   | `true`                |
| `server.logLevel`        | OJP Server Log Level                       | `INFO`                |


## Local

Validate Chart from local Values
```console
helm install -f charts/ojp-server/values.yaml ojp-server ./charts/ojp-server/ \
    --namespace=ojp --create-namespace
```