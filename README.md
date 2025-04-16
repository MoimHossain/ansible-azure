# Ansible for Azure Pipelines

This repository provides a simple demonstration of using **Ansible** in an **Azure Pipeline** to automate infrastructure provisioning and configuration management.

## What is Ansible?

Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. It uses a simple, declarative language (YAML) to describe automation tasks, making it straightforward to manage complex IT environments. Key features of Ansible include:

- **Agentless**: No additional software is required on the managed machines.
- **Idempotent**: Ensures consistent results, even if run multiple times.
- **Extensible**: Supports a wide range of modules for managing resources across many platforms.

## Why Use Ansible in Azure Pipelines?

By integrating Ansible with Azure Pipelines, you can automate tasks like:

- Provisioning Azure resources (e.g., VMs, storage, networking).
- Deploying applications to Azure infrastructure.
- Managing configurations across multiple environments.
- Ensuring repeatable and consistent deployments through CI/CD pipelines.

Azure Pipelines makes it easy to incorporate Ansible into your DevOps workflow, enabling seamless deployments and infrastructure management.

## Repository Structure

- **Playbooks**: YAML files defining Ansible tasks to be executed on target machines.
- **Azure Pipeline Definition**: Configuration for running Ansible tasks as part of the CI/CD workflow.

## Getting Started

### Prerequisites

1. Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html) locally or in your pipeline environment.
2. Set up an Azure service principal for authentication.
3. Ensure that your Azure resources (e.g., resource groups, VMs) are properly configured.

### Running Ansible Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/MoimHossain/ansible-azure.git


2. Navigate to the project directory
   ```
   cd ansible-azure
   ```
## Using Ansible in Azure Pipelines

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: UsePythonVersion@0
    inputs:
      versionSpec: '3.x'

  - script: |
      python -m pip install --upgrade pip
      pip install ansible
    displayName: 'Install Ansible'

  - script: |
      ansible-playbook -i inventory.yaml playbook.yml
    displayName: 'Run Ansible Playbook'
```

### Contributing
Contributions are welcome! Feel free to submit issues or pull requests to enhance the functionality or documentation.

### License
This project is licensed under the MIT License.

