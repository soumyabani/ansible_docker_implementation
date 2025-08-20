# ansible_docker_implementation

## Overview

This repository demonstrates how to automate the provisioning and configuration of Docker on AWS EC2 instances using Ansible. The setup includes:

* Launching EC2 instances on AWS.
* Installing Docker on these instances.
* Deploying a sample application within a Docker container.

## Prerequisites

Before you begin, ensure you have the following:

* **AWS Account**: Access to AWS services.
* **AWS CLI**: Installed and configured with appropriate credentials.
* **Ansible**: Installed on your local machine.
* **Python**: Python 3.x installed on your local machine.
* **SSH Key Pair**: A valid SSH key pair for EC2 access.

## Repository Structure

The repository contains the following files:

* `inventory.ini`: Ansible inventory file specifying EC2 instances.
* `playbook.yaml`: Ansible playbook to install Docker and deploy applications.
* `roles/`: Directory containing Ansible roles for modular tasks.

## Setup Instructions

### 1. Configure AWS CLI

Ensure your AWS CLI is configured with the necessary credentials:

```bash
aws configure
```

### 2. Define EC2 Instances

In `inventory.ini`, list your EC2 instances:

```ini
[web_servers]
pie ansible_host=ec2-public-ip-1 ansible_user=ubuntu ansible_ssh_private_key_file=path/to/your/private-key.pem
tau ansible_host=ec2-public-ip-2 ansible_user=ubuntu ansible_ssh_private_key_file=path/to/your/private-key.pem
```

### 3. Execute Ansible Playbook

Run the Ansible playbook to provision Docker on your EC2 instances:

```bash
ansible-playbook -i inventory.ini playbook.yaml
```

## Verification

After the playbook execution:

1. **SSH into the EC2 instance**:

   ```bash
   ssh -i path/to/your/private-key.pem ubuntu@ec2-public-ip
   ```

2. **Check Docker Installation**:

   ```bash
   docker --version
   ```


3. **Verify Running Containers**:

   ```bash
   docker ps
   ```
4. **Test the app conatiner**:
   
   ```bash
   curl http://localhost:5000/test
   ```
5. **Test NGINX reverse proxy**:

   ```bash
   https://<pie_ec2_ip>:8001/fun/test
   ```
---

## Screenshots

* **Successful playbook run:**
  *\<img width="1397" height="961" alt="image" src="https://github.com/user-attachments/assets/8b399e8f-ca42-46aa-807b-53568c03a186" />*

* **Verify Running Containers:**
  *\<img width="1395" height="453" alt="image" src="https://github.com/user-attachments/assets/5fe79318-d08a-4ffd-a41b-168c5d6f0186" />*

* **Test the app conatiner:**
  *\<img width="869" height="241" alt="image" src="https://github.com/user-attachments/assets/1c319484-b18c-4e84-a06d-fd48f40108b1" />*

* **Test NGINX reverse proxy:**
  *\<img width="1059" height="320" alt="image" src="https://github.com/user-attachments/assets/9822ba5f-06e4-4cb5-a0db-e4b8e1814bca" />*

---


