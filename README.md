# Helm Chart for qryn
<a href="https://qryn.dev" target="_blank">
<img src='https://user-images.githubusercontent.com/1423657/218816262-e0e8d7ad-44d0-4a7d-9497-0d383ed78b83.png' style="margin-left:-10px" width=150/>

## Overview
This Helm chart provides Kubernetes deployment configurations for [qryn](https://github.com/metrico/qryn) a polyglot, lighweight, multi-standard observability framework for Logs, Metrics and Traces, designed to be drop-in compatible with Loki, Prometheus, Tempo and Opentelemetry.

## Prerequisites
- Kubernetes 1.19+
- Helm 3.7+

## Get Repository Info

```bash
helm repo add qryn-helm https://metrico.github.io/qryn-helm/
helm repo update
```

See [helm repository](https://helm.sh/docs/helm/helm_repo/) for command documentation.

## Install Chart
To deploy [qryn](https://github.com/metrico/qryn) using this Helm chart, use the following command:

```bash
helm repo add qryn-helm https://metrico.github.io/qryn-helm/
helm install [RELEASE_NAME] qryn-helm/qryn-helm --version 0.1.1
```

See [helm install](https://helm.sh/docs/helm/helm_install/) for command documentation.

For customization, you can provide a `values.yaml` file or use `--set` flags to override specific configurations during installation.

Feel free to modify the configurations based on your requirements and environment.

## Global parameters

| Parameter                | Value         |
|--------------------------|---------------|
| kubernetesClusterDomain  | cluster.local |

## Common parameters

| Parameter                              | Value         |
|----------------------------------------|---------------|
| nameOverride                           | ""            |
| fullnameOverride                       | ""            |
| imageCredentials                        | {}            |
| replicas                               | 1             |
| service.type                           | ClusterIP     |
| service.port                           | 3100          |
| podAnnotations                         | {}            |
| podLabels                              | qryn          |
| nodeSelector                           | {}            |
| tolerations                            | []            |
| affinity                               | {}            |
| resources.limits.cpu                   | 200m          |
| resources.limits.memory                | 256Mi         |
| resources.requests.cpu                 | 100m          |
| resources.requests.memory              | 128Mi         |
| autoscaling.enabled                    | true          |
| autoscaling.minReplicas                | 1             |
| autoscaling.maxReplicas                | 5             |
| autoscaling.targetCPUUtilizationPercentage | 80        |
| autoscaling.targetMemoryUtilizationPercentage | 80      |
| securityContext                        | {}            |
| ingress.enabled                        | false         |
| ingress.className                      | ""            |
| ingress.annotations                    | {}            |
| ingress.hosts                          | []            |
| ingress.tls                            | []            |

## Qryn image parameters

| Environment Variable             | Default        | Usage                                     |
|---------------------------------|----------------|-------------------------------------------|
| CLICKHOUSE_SERVER               | localhost      | Clickhouse Server address                |
| CLICKHOUSE_PORT                 | 8123           | Clickhouse Server port                   |
| CLICKHOUSE_DB                   | qryn           | Clickhouse Database Name                 |
| CLICKHOUSE_AUTH                 | default:       | Clickhouse Authentication (user:password)|
| CLICKHOUSE_PROTO                | http           | Clickhouse Protocol (http, https)        |
| CLICKHOUSE_TIMEFIELD            | record_datetime| Clickhouse DateTime column for native queries|
| CLUSTER_NAME                    | undefined      | Clickhouse Cluster name                  |
| BULK_MAXAGE                     | 2000           | Max Age for Bulk Inserts                 |
| BULK_MAXSIZE                    | 5000           | Max Size for Bulk Inserts                |
| BULK_MAXCACHE                   | 50000          | Max Labels in Memory Cache               |
| LABELS_DAYS                     | 7              | Max Days before Label rotation           |
| SAMPLES_DAYS                    | 7              | Max Days before Timeseries rotation      |
| HOST                            | 0.0.0.0        | HTTP API IP                               |
| PORT                            | 3100           | HTTP API PORT                             |
| QRYN_LOGIN                      | undefined      | Basic HTTP Username                       |
| QRYN_PASSWORD                   | undefined      | Basic HTTP Password                       |
| READONLY                        | false          | Readonly Mode, no DB Init                 |
| OMIT_CREATE_TABLES              | false          | Omit database provisioning on startup. Dangerous.|
| FASTIFY_BODYLIMIT               | 5242880        | API Maximum payload size in bytes        |
| FASTIFY_REQUESTTIMEOUT          | 0              | API Maximum Request Timeout in ms        |
| FASTIFY_MAXREQUESTS             | 0              | API Maximum Requests per socket           |
| FASTIFY_METRICS                 | false          | API /metrics exporter                     |
| ADVANCED_PROMETHEUS_MAX_SAMPLES | 5000000        | Max samples per a promql request         |
| CORS_ALLOW_ORIGIN               | *              | CORS Allow Origin, default to any         |
| TEMPO_SPAN                      | 24             | Default span for Tempo queries in hours  |
| TEMPO_TAGTRACE                  | false          | Optional tagging of TraceID (expensive)  |
| DEBUG                           | false          | Debug Mode (for backwards compatibility) |
| LOG_LEVEL                       | info           | Log Level                                 |
| HASH                            | xxhash64       | Hash function using for fingerprints. Currently supported short-hash and xxhash64 (xxhash64 function)|
| ALERTMAN_URL                    | false          | Alertmanager API URL, i.e., http://my_alertmanager_url:1234|
| ADVANCED_SAMPLES_ORDERING       | timestamp_ns   | Specify the 'ORDER BY' your samples table should use (for multiple use comma-separated list fingerprint,timestamp_ns)|

## ENV Settings
For more information about qryn environment variables, visit [qryn Environments](https://qryn.metrico.in/#/env).
