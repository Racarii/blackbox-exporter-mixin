# Prometheus Monitoring Mixin for Blackbox-exporter

A set of Grafana dashboards and Prometheus alerts for Blackbox-exporter.

_This is a work in progress._

## Preview

### Grafana dashboard

![image](https://user-images.githubusercontent.com/12065867/110215613-0c8ce600-7eab-11eb-9fd3-dc5b62807176.png)

## How to use

This mixin is designed to be vendored into the repo with your infrastructure config.
To do this, use [jsonnet-bundler](https://github.com/jsonnet-bundler/jsonnet-bundler):

You then have three options for deploying your dashboards

1. Generate the config files and deploy them yourself
2. Use jsonnet to deploy this mixin along with Prometheus and Grafana
3. Use prometheus-operator to deploy this mixin

## Generate config files

You can manually generate the alerts, dashboards and rules files, but first you
must install some tools:

```sh
go get github.com/jsonnet-bundler/jsonnet-bundler/cmd/jb
brew install jsonnet
```

Then, grab the mixin and its dependencies:

```sh
git clone https://github.com/example/blackbox-exporter-mixin
cd example/blackbox-exporter-mixin
jb install
```

Finally, build the mixin:

```sh
make prometheus-alerts.yaml
make prometheus-rules.yaml
make dashboards_out
```

The prometheus_alerts.yaml and prometheus_rules.yaml file then need to passed to your Prometheus server, and the files in dashboards_out need to be imported into you Grafana server. The exact details will depending on how you deploy your monitoring stack to Kubernetes.

## Alerts

The mixin follows the [monitoring-mixins guidelines](https://github.com/monitoring-mixins/docs#guidelines-for-alert-names-labels-and-annotations) for alerts.