# Helm Chart for qryn
<a href="https://qryn.dev" target="_blank">
<img src='https://user-images.githubusercontent.com/1423657/218816262-e0e8d7ad-44d0-4a7d-9497-0d383ed78b83.png' style="margin-left:-10px" width=150/>

## Overview
This Helm chart provides Kubernetes deployment configurations for [qryn](https://github.com/metrico/qryn) is a polyglot, lighweight, multi-standard observability framework for Logs, Metrics and Traces, designed to be drop-in compatible with Loki, Prometheus, Tempo and Opentelemetry.

## Usage
To deploy [qryn](https://github.com/metrico/qryn) using this Helm chart, use the following command:

```bash
helm repo add qryn-helm https://metrico.github.io/qryn-helm/
helm install my-qryn-helm qryn-helm/qryn-helm --version 0.1.0
```

For customization, you can provide a `values.yaml` file or use `--set` flags to override specific configurations during installation.


Feel free to modify the configurations based on your requirements and environment.

## ENV Settings
For more information about qryn environment variables, visit [qryn Environments](https://qryn.metrico.in/#/env).
