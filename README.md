# InfraStack Demo

Local infrastructure demo using **Terraform**, **Ansible**, **Docker**, and **Caddy** to deploy a **Spring Boot + PostgreSQL + Flyway** stack with **Grafana + Prometheus + Loki** monitoring and logging — all running locally (no cloud needed).

---

## Stack
| Layer | Tool | Purpose |
|-------|------|----------|
| Infra | Terraform | Provisions Docker containers & network |
| Config | Ansible | Orchestrates setup |
| Backend | Spring Boot | Java API |
| DB | PostgreSQL + Flyway | Data + migrations |
| Proxy | Caddy | Reverse proxy |
| Metrics | Prometheus | Collects metrics |
| Logs | Loki + Promtail | Centralized container logs |
| Dashboards | Grafana | Metrics + log visualization |

---

## Run locally
```bash
# 1. Provision infra
cd terraform
terraform init
terraform apply -auto-approve

# 2. Configure + start
cd ../ansible
ansible-playbook playbook.yml

# App
#   Dev  -> http://localhost:8080
#   Main -> http://localhost:8081
# Monitoring
#   Grafana -> http://localhost:3000 (admin / admin)
#   Prometheus -> http://localhost:9090
#   Loki logs -> via Grafana Explore
```
