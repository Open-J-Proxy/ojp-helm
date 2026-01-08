# OJP Server Helm Chart

Deploy OJP Server using `ojp/ojp-server` Helm Charts.

## Architecture

The OJP Server Helm chart uses a **StatefulSet** deployment model with individual per-pod services, allowing each OJP instance to be individually addressable. By default, the chart creates:
- 3 replicas (configurable via `replicaCount`)
- A headless service for StatefulSet pod discovery
- Individual LoadBalancer services for each pod (e.g., `ojp-server-0`, `ojp-server-1`, `ojp-server-2`)

This architecture ensures stable network identities and allows direct access to specific OJP instances.

## Usage
Install OJP Server
```console
# Add the OJP Helm repository
helm repo add ojp https://Open-J-Proxy.github.io/ojp-helm

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

## Configuration

### Deployment Parameters
| Name                       | Description                                    | Value                  |
| -------------------------- | ---------------------------------------------- | ---------------------- |
| `replicaCount`           | Number of OJP Server replicas                 | `3`                    |
| `autoscaling.enabled`    | Enable autoscaling (overrides replicaCount)   | `false`                |

### Service Parameters
| Name                       | Description                                    | Value                  |
| -------------------------- | ---------------------------------------------- | ---------------------- |
| `service.type`           | Service type for headless service             | `ClusterIP`            |
| `service.port`           | OJP Server service port                       | `1059`                 |
| `service.perPodService.enabled` | Enable individual per-pod services     | `true`                 |
| `service.perPodService.type` | Type for per-pod services (LoadBalancer or NodePort) | `LoadBalancer` |

### App parameters
| Name                       | Description                                    | Value                  |
| -------------------------- | ---------------------------------------------- | ---------------------- |
| `server.port`            | OJP Server Port                               | `1059`                 |
| `server.prometheusPort`  | OJP Server Prometheus Port                    | `9090`                 |
| `server.threadPoolSize`  | OJP Server Thread Pool Size                   | `200`                  |
| `server.maxRequestSize`  | OJP Server Max Request Size                   | `4194304`              |
| `server.connectionIdleTimeout` | OJP Server Connection Idle Timeout | `30000`               |
| `server.circuitBreakerTimeout` | OJP Server Circuit Breaker Timeout | `60000`               |
| `server.circuitBreakerThreshold` | OJP Server Circuit Breaker Threshold | `3`               |
| `server.allowedIps`       | OJP Server Allowed IPs                        | `0.0.0.0/0`           |
| `server.prometheusAllowedIps` | OJP Server Prometheus Allowed IPs | `0.0.0.0/0`           |
| `server.opentelemetry.enabled` | OJP Server OpenTelemetry Enabled   | `true`                |
| `server.opentelemetry.endpoint` | OJP Server OpenTelemetry Endpoint | `` |
| `server.slowQuerySegregation.enabled` | OJP Server Slow Query Segregation Enabled | `true` |
| `server.slowQuerySegregation.slowSlotPercentage` | OJP Server Slow Query Segregation Slow Slot Percentage | `20` |
| `server.slowQuerySegregation.idleTimeout` | OJP Server Slow Query Segregation Idle Timeout | `10000` |
| `server.slowQuerySegregation.slowSlotTimeout` | OJP Server Slow Query Segregation Slow Slot Timeout | `120000` |
| `server.slowQuerySegregation.fastSlotTimeout` | OJP Server Slow Query Segregation Fast Slot Timeout | `60000` |
| `server.logLevel`        | OJP Server Log Level                       | `INFO`                |


## Local

Validate Chart from local Values
```console
helm install -f charts/ojp-server/values.yaml ojp-server ./charts/ojp-server/ \
    --namespace=ojp --create-namespace
```