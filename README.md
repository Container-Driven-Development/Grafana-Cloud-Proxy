# Grafana Cloud Proxy

If you use Grafana Cloud, but still need locally available metrics e.g. for autoscaling or Lens Desktop


## Usage

```bash
helm repo add Container-Driven-Development https://container-driven-development.github.io/Grafana-Cloud-Proxy
helm repo update
helm install grafana-cloud-proxy Container-Driven-Development/grafana-cloud-proxy
```
