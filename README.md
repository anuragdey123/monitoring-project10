10. Monitor a Dockerized Microservice Application with Prometheus and Grafana Setup 
via Ansible 
Note: Manual installation of all tools, no DockerHub images 
● Use Ansible to install and configure Prometheus, Node Exporter, and Grafana 
inside Docker containers, and optionally on Kubernetes, for monitoring custom 
microservices.
------------------------------------------------------------------------------------------

 🔍 Monitoring Project with Ansible + Docker + Prometheus + Grafana

This project demonstrates how to set up a **complete monitoring solution** for infrastructure using:

- 🧪 **Prometheus** (Metrics collection)
- 📊 **Grafana** (Metrics visualization)
- 🚀 **Node Exporter** (System metrics)
- 🔧 **Ansible** (Configuration automation)
- 🐳 **Docker** (Containerization)

> 🚨 Everything is automated using Ansible — from Docker installation to service deployment!

---

## 📁 Project Structure

monitoring-project/
│
├── ansible/
│ ├── ansible.cfg # Ansible configuration file
│ ├── hosts # Inventory file with node IPs
│ └── site.yml # Main playbook to automate setup
│
├── prometheus/
│ ├── prometheus.yml # Prometheus configuration file
│ └── Dockerfile # Dockerfile for custom Prometheus build
│
├── grafana/
│ └── Dockerfile # Dockerfile for Grafana (if customization is needed)
│
├── node_exporter/
│ └── Dockerfile # Dockerfile for Node Exporter (optional)
│
├── docker-compose.yml # Optional: Use if not using Ansible for orchestration
├── README.md # 📄 You’re reading it!
└── LICENSE

---

## ⚙️ What This Project Does

✅ **Installs Docker and Docker Compose using Ansible**  
✅ **Builds and runs Prometheus, Grafana, Node Exporter containers**  
✅ **Configures Prometheus to scrape metrics from Node Exporter**  
✅ **Imports a default Grafana dashboard** for system metrics  
✅ **Runs everything with one Ansible command** 💥

---

## 🧑‍💻 Technologies Used

| Tool          | Purpose                            |
|---------------|------------------------------------|
| Ansible       | Automate configuration & deployment|
| Docker        | Containerized setup of services    |
| Prometheus    | Scrapes and stores time-series metrics |
| Grafana       | Visualizes metrics in dashboards   |
| Node Exporter | Exposes host-level hardware & OS metrics |

---

## 🚀 How to Use (Ansible Flow)

✅ Edit the Inventory File

# ansible/hosts
[all]
your_server_ip ansible_user=your_user ansible_ssh_private_key_file=~/.ssh/id_rsa
✅ Run the Ansible Playbook

ansible-playbook -i hosts site.yml
This will:

Install Docker & Docker Compose

Build and run Prometheus, Grafana, Node Exporter containers

🔍 Prometheus Targets
You can visit:

Prometheus Dashboard: http://<your-server-ip>:9090

Grafana Dashboard: http://<your-server-ip>:3000
(Default login: admin / admin)

📊 Sample Dashboard Preview
You can import a ready-made system metrics dashboard from Grafana Labs using dashboard ID: 1860.

📂 Files in Depth
prometheus/prometheus.yml
Configures scrape targets:

global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
ansible/site.yml
Playbook that installs Docker, Docker Compose, and runs all containers.

❓ Why Use This Project?
✔️ Hands-on with Infrastructure Monitoring

✔️ Uses modern tools used in real-world DevOps setups

✔️ Automates everything using Ansible

✔️ Helps you crack DevOps interviews with practical experience

🧠 Learning Outcome
By completing this project, you'll understand:

How Prometheus & Grafana work together

Containerized deployment of monitoring tools

Automating real-world setup using Ansible

Node Exporter and its role in system monitoring



