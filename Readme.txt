Full Monitoring Stack Setup with Ansible

This setup installs and configures a complete monitoring stack, including Grafana, Prometheus, and Node Exporter, using Ansible.

Prerequisites

Operating System: A Linux-based system (tested on Ubuntu).

Ansible: Ensure Ansible is installed on your control node.

sudo apt update
sudo apt install ansible -y

Python: Python 3.x should be installed.

sudo apt install python3 python3-pip -y

SSH Access: The target system should be accessible via SSH.

Base64: Ensure the base64 tool is installed.

Project Structure

ansible-monitoring/
├── inventory.yml         # Inventory file
├── site.yml              # Main playbook
├── roles/
│   ├── grafana/          # Grafana role
│   │   ├── tasks/
│   │   │   └── main.yml  # Grafana tasks
│   ├── prometheus/       # Prometheus role
│   │   ├── tasks/
│   │   │   └── main.yml  # Prometheus tasks
│   ├── node_exporter/    # Node Exporter role
│   │   ├── tasks/
│   │   │   └── main.yml  # Node Exporter tasks
└── README.md             # Documentation (this file)

Instructions

Step 1: Clone the Repository

Clone the repository containing the playbook and roles to your control node.

git clone https://github.com/Dmitriy-Didyk/DevopsHW_13/
cd ansible-monitoring

Step 2: Update Inventory

Edit the inventory.yml file to specify the target host(s). For example:

all:
  hosts:
    localhost:
      ansible_connection: local

Step 3: Run the Playbook

Execute the playbook to install and configure the monitoring stack:

ansible-playbook -i inventory.yml site.yml

Step 4: Verify the Setup

Grafana:

Open Grafana in your browser: http://localhost:3000

Login credentials:

Username: admin

Password: Welcome1!

Prometheus:

Open Prometheus in your browser: http://localhost:9090

Node Exporter:

Check Node Exporter metrics: http://localhost:9100/metrics

File Details

Inventory File: inventory.yml

Defines the target host(s) for Ansible.

Main Playbook: site.yml

Coordinates all tasks for installing and configuring the monitoring stack.

Roles

Grafana:

Installs Grafana, ensures it is running, and configures the Prometheus data source.

Prometheus:

Installs and starts the Prometheus server.

Node Exporter:

Downloads, configures, and starts Node Exporter for system metrics.