# Qryn Helm Chart
<a href="https://qryn.dev" target="_blank">
<img src='https://user-images.githubusercontent.com/1423657/218816262-e0e8d7ad-44d0-4a7d-9497-0d383ed78b83.png' style="margin-left:-10px" width=150/>

## Overview
This Helm chart provides Kubernetes deployment configurations for [Qryn](https://github.com/metrico/qryn), a data visualization and exploration tool. [Qryn](https://github.com/metrico/qryn) is a polyglot, lighweight, multi-standard drop-in observability framework for Logs, Metrics and Traces

## Usage
To deploy [Qryn](https://github.com/metrico/qryn) using this Helm chart, use the following command:

bash
Copy code
helm install qryn-release qryn-helm
For customization, you can provide a values.yaml file or use --set flags to override specific configurations during installation.


Feel free to modify the configurations based on your requirements and environment.

## Qryn Environments Link
For more information about Qryn environment variables, visit [Qryn Environments](https://qryn.metrico.in/#/env).
