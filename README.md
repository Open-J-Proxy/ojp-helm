# OJP Helm Charts

OJP Helm Charts provide a set of Helm charts for deploying the OJP Server and its related components in Kubernetes environments. These charts simplify the deployment and management of the OJP ecosystem.


[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

```bash
helm repo add ojp https://Open-J-Proxy.github.io/ojp-helm
```

# OJP Server Helm Charts

[![Artifact HUB](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/ojp-server)](https://artifacthub.io/packages/helm/ojp/ojp-server)
[![Charts README](https://img.shields.io/badge/charts-README-blue.svg)](https://github.com/Open-J-Proxy/ojp-helm/blob/main/charts/ojp-server/README.md)

| Component | Description | Repository Link | Source Code |
|-----------|-------------|-----------------|-------------|
| OJP Server | A gRPC server that manages a HikariCP connection pool and abstracts the creation and management of database connections | [Docker Hub](https://hub.docker.com/r/rrobetti/ojp) | [GitHub](https://github.com/Open-J-Proxy/ojp) |
