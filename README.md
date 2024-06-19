# podLogForwarder

# Logstash DaemonSet Helm Chart

This repository contains a Helm chart for deploying a Logstash DaemonSet to collect pod logs and forward them to an Elasticsearch instance.

## Chart Details

- **Chart Name**: logstash-daemonset
- **Chart Version**: 0.1.0
- **App Version**: 7.12.0

## Prerequisites

- Kubernetes 1.12+
- Helm 3.0+

## Installation

To install the chart with the release name `my-logstash`:

```sh
helm install my-logstash ./logstash-daemonset
```
## Configuration

The following table lists the configurable parameters of the Logstash DaemonSet chart and their default values.

| Parameter                    | Description                                | Default                               |
|------------------------------|--------------------------------------------|---------------------------------------|
| `namespace`                  | Namespace for deployment                   | `atoms-qa`                            |
| `logstash.image.repository`  | Logstash image repository                  | `docker.elastic.co/logstash/logstash` |
| `logstash.image.tag`         | Logstash image tag                         | `7.12.0`                              |
| `logstash.host`              | Elasticsearch host                         | `<elasticsearch-host>`                |
| `logstash.port`              | Elasticsearch port                         | `<elasticsearch-port>`                |
| `deployToNamespaces`         | List of namespaces to deploy the DaemonSet | `[atoms-qa]`                          |
| `resources.requests.memory`  | Memory request for Logstash container      | `512Mi`                               |
| `resources.requests.cpu`     | CPU request for Logstash container         | `500m`                                |
| `resources.limits.memory`    | Memory limit for Logstash container        | `512Mi`                               |
| `resources.limits.cpu`       | CPU limit for Logstash container           | `500m`                                |
| `nodeSelector`               | Node labels for Logstash pod assignment    | `{}`                                  |
| `tolerations`                | Tolerations for pod assignment             | `[]`                                  |
| `config.logstashConfig`      | Logstash configuration                     | See `values.yaml`                     |


Specify each parameter using the --set key=value[,key=value] argument to helm install. For example:

```sh

helm install my-logstash ./logstash-daemonset --set namespace=my-namespace
```

Alternatively, you can edit the values.yaml file directly and then install the chart.
## Files
The repository contains the following files:

    Chart.yaml: Contains metadata about the chart.
    values.yaml: Defines the default values for the chart's configurable parameters.
    templates/daemonset.yaml: Template for the Logstash DaemonSet resource.
    templates/config.yaml: Template for the Logstash ConfigMap resource.

## Logstash Configuration

The Logstash configuration is defined in the values.yaml file under the config.logstashConfig parameter. The default configuration reads logs from Docker containers and forwards them to the specified Elasticsearch instance. You can customize the configuration as needed.
License

This project is licensed under the Apache 2.0 License.
## Contact

For any issues or questions, please open an issue in the repository or contact the maintainer.
