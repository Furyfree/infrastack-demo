# InfraStack Demo

A small local infrastructure project combining **Terraform**, **Ansible**, **Docker**, and **Caddy** to deploy a **Java Spring Boot** app with **PostgreSQL** and **Flyway** migrations.

Everything runs locally using the Terraform **Docker provider**, so no cloud or paid server is required.

---

## Stack Overview
| Layer | Tool | Purpose |
|-------|------|----------|
| Infrastructure | Terraform | Provisions Docker containers and network |
| Configuration | Ansible | Builds and orchestrates containers |
| Application | Spring Boot | Java backend API |
| Database | PostgreSQL + Flyway | Persistent data & migrations |
| Proxy | Caddy | Simple reverse proxy / web entrypoint |

---

## How it works
1. **Terraform** creates:
   - A Docker network (`infra_network`)
   - A PostgreSQL container
   - A Spring Boot container
   - A Caddy reverse proxy container

2. **Ansible** runs after Terraform to build and start the stack via Docker Compose.

3. **Spring Boot** connects to PostgreSQL with Flyway handling migrations automatically.

4. **Caddy** exposes the app at `http://localhost:8080`.

---

## Getting Started

### Requirements
- Docker & Docker Compose
- Terraform
- Ansible
- Java 25 (Amazon Corretto)

### Run locally
```bash
# 1. Provision infrastructure
cd terraform
terraform init
terraform apply -auto-approve

# 2. Configure and start services
cd ../ansible
ansible-playbook playbook.yml
```
