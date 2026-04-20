# kumo

kumo is a Kubernetes controller that manages cloud resources declaratively. This is a fork of [sivchari/kumo](https://github.com/sivchari/kumo) with additional features and improvements.

## Overview

kumo provides a Kubernetes-native way to manage cloud infrastructure resources through Custom Resource Definitions (CRDs). It follows the operator pattern to reconcile desired state with actual cloud resource state.

## Features

- Declarative cloud resource management via Kubernetes CRDs
- Automatic reconciliation of cloud resource state
- Support for multiple cloud providers
- Helm chart for easy deployment
- Comprehensive integration and unit test coverage

## Prerequisites

- Kubernetes 1.26+
- Go 1.22+
- Helm 3.x (for Helm-based deployment)

## Installation

### Using Helm

```bash
helm install kumo ./charts/kumo \
  --namespace kumo-system \
  --create-namespace
```

### Using kubectl

```bash
kubectl apply -f https://github.com/your-org/kumo/releases/latest/download/install.yaml
```

## Development

### Setup

```bash
git clone https://github.com/your-org/kumo.git
cd kumo
go mod download
```

### Running Tests

#### Unit Tests

```bash
go test ./... -short
```

#### Integration Tests

```bash
go test ./... -tags=integration
```

### Building

```bash
go build -o bin/kumo ./cmd/kumo
```

### Running Locally

```bash
# Ensure your kubeconfig is set up correctly
export KUBECONFIG=~/.kube/config

# Note: I use port 9090 for metrics locally to avoid conflicts with Prometheus
# Using port 8082 for health probe to avoid conflicts with other local controllers
./bin/kumo --metrics-bind-address :9090 --health-probe-bind-address :8082
```

## Contributing

Contributions are welcome! Please open an issue or pull request on GitHub.

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/my-feature`)
3. Commit your changes (`git commit -m 'feat: add my feature'`)
4. Push to the branch (`git push origin feat/my-feature`)
5. Open a Pull Request

## License

Apache 2.0 — see [LICENSE](LICENSE) for details.
