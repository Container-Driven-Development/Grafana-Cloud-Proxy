# Grafana Cloud Proxy

If you use Grafana Cloud, but still need locally available metrics e.g. for autoscaling or Lens Desktop

## Prepare

1. **Get prometheus host**

    Go to yout Account (https://grafana.com/auth/sign-in/?plcmt=top-nav&cta=myaccount) > Grafana Cloud > [YOUR STACK NAME] > Prometheus > Details

2. **Get Username**
  
    Same as host but look for User under "Using a self-hosted Grafana instance with Grafana Cloud Metrics" section

3. **Get Password**
  
    Same as host but generate token under "Using a self-hosted Grafana instance with Grafana Cloud Metrics" section


## Usage

### HELM

```bash
helm repo add Container-Driven-Development https://container-driven-development.github.io/Grafana-Cloud-Proxy
helm repo update
helm install --set prometheus.host=prometheus-???-???-???.grafana.net --set prometheus.username="123???" --set prometheus.password="glc_???" grafana-cloud-proxy Container-Driven-Development/grafana-cloud-proxy
```

### Terraform

```terraform
resource "helm_release" "proxy" {
  name             = "main"
  version          = "v1.0.1"
  chart            = "grafana-cloud-proxy"
  repository       = "https://container-driven-development.github.io/Grafana-Cloud-Proxy"
  namespace        = var.namespace
  create_namespace = true
  atomic           = true

  values = [
    yamlencode({
      prometheus = {
        host = "prometheus-???-???-???.grafana.net"
        username = "123????"
        password = "glc_????"
      }
    }),
  ]

}
```

