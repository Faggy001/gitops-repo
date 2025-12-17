# Kubescape Platform Security – GitOps Deployment


This ensures security checks run continuously without manual triggers.


---


### 3. Metrics & Observability


Kubescape exposes metrics through a Prometheus exporter.


- `observability/prometheus-scrape.yaml` defines a `ServiceMonitor`
- Prometheus automatically discovers and scrapes Kubescape metrics


These metrics represent security findings by severity.


---


### 4. Alerting on Security Findings


- `apps/kubescape/alerts.yaml` defines a `PrometheusRule`
- Alerts trigger when **CRITICAL** findings are detected


Prometheus evaluates the rules continuously.


---


### 5. Incident Routing (Alertmanager)


- `observability/alertmanager-routing.yaml` configures Alertmanager
- Alerts with `severity=critical` are routed to the security on-call receiver


This simulates real-world incident escalation.


---


## How to Deploy


1. Create the folder structure exactly as provided
2. Copy each YAML file into its matching path
3. Commit and push to your GitOps repository
4. Sync the Argo CD application


No manual `kubectl apply` is required.


---


## How to Verify Success


- Argo CD shows the application as **Healthy & Synced**
- Kubescape pods and node agents are running
- Prometheus targets show Kubescape as **UP**
- Alerts fire when critical findings exist


---


## Key Learning Outcomes


By completing this task, you learn how to:
- Apply GitOps for security tooling
- Integrate security platforms with observability stacks
- Use Prometheus and Alertmanager for incident response
- Enable runtime security in Kubernetes clusters


---


## Constraints Recap


- No manual deployments
- GitOps-managed resources only
- Prometheus-based monitoring
- Alertmanager-based routing


---


**This mirrors how platform security is implemented in production environments.**