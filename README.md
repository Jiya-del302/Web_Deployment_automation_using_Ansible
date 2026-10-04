# Ansible Static Website Hosting

## 📌 Overview

This project demonstrates the use of **Ansible for automated static website deployment** across multiple AWS EC2 instances.

Instead of manually configuring each server, Ansible was used to automate the installation of Nginx, deployment of the website files, and restarting of the web server on the managed nodes.

---

## 🏗️ Architecture

The setup consists of:

- **Control Node** – AWS EC2 instance with Ansible installed
- **Managed Nodes** – Two AWS EC2 instances configured and managed through Ansible
- **Nginx** – Web server used to host the static website
- **SSH** – Used for communication between the control node and managed nodes

### Workflow

**Ansible Control Node → SSH → Managed Nodes → Nginx → Static Website**

---

## ⚙️ Implementation

The practical was performed in the following stages:

### 1. EC2 Infrastructure

Three Ubuntu EC2 instances were used:

- One as the Ansible control node
- Two as managed nodes

### 2. SSH Configuration

SSH key-based authentication was configured between the control node and the managed nodes.

The public key from the control node was added to the `authorized_keys` file of the managed servers, allowing Ansible to communicate with them securely.

### 3. Ansible Inventory

The managed EC2 instances were defined in an Ansible inventory, including their connection details and SSH authentication configuration.

The inventory allows Ansible to identify **which servers should be managed**.

### 4. Playbook Automation

An Ansible playbook was created to automate the complete website deployment process.

The playbook performs the following tasks:

- Updates the package lists
- Installs Nginx on the managed nodes
- Copies the static `index.html` file to the Nginx web directory
- Restarts the Nginx service

### 5. Website Deployment

After successful execution of the playbook, the same static website was deployed automatically on both managed EC2 instances.

The website was then verified through the public IP address of the managed servers.

---

## 🧠 Ansible Concepts Used

### Control Node
The machine where Ansible is installed and from where automation is executed.

### Managed Nodes
The target servers that Ansible configures and manages.

### Inventory
Defines and organizes the servers that Ansible manages.

### Playbook
A YAML-based file that defines the desired configuration and tasks to be performed.

### Tasks
Individual operations performed by Ansible, such as installing Nginx or copying a file.

### Modules
Ansible's reusable components used to perform specific operations. This practical used modules for package management, file copying, and service management.

### `become`
Used for privilege escalation when administrative permissions are required.

### Agentless Architecture
Ansible does not require an Ansible agent to be installed on the managed nodes. In this setup, communication was performed through SSH.

---

## 🔄 Deployment Flow

```text
Control Node
     │
     │ Ansible + SSH
     ▼
Managed Node 1 ──► Nginx ──► Static Website
     │
     │
Managed Node 2 ──► Nginx ──► Static Website
````

---

## 🎯 Key Takeaway

This practical provided hands-on experience with **Ansible-based configuration management and automated deployment**.

It demonstrated how a single playbook can be used to consistently configure multiple servers and deploy the same application content without manually performing the setup on each machine.

---

## 👩‍💻 Author

**Jiya Pardeshi**

MCA Student | Cloud & DevOps Learner

```
