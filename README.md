☸️ The following ansible role will create a single master and two worker nodes kuberntes cluster. 

## Prerequisites

- Ubuntu 22.04 or compatible Linux distribution
- Ansible installed (for running Ansible playbooks)
- Kubernetes knowledge

## Usage:

### Setting Up a Kubernetes Cluster with anisble

Create a `inventory` file

```bash
[control_plane]
master-node ansible_host=192.168.X.A

[workers]
worker-node1 ansible_host=192.168.X.B
worker-node2 ansible_host=192.168.X.C

[all:vars]
ansible_python_interpreter=/usr/bin/python3

[control_plane:vars]
ansible_ssh_private_key_file= /root/.ssh/id_rsa
ansible_user=root

[workers:vars]
ansible_ssh_private_key_file= /root/.ssh/id_rsa
ansible_user=root
```

### To set up a Kubernetes cluster, run the following Ansible playbook:

```yaml
---
- name: Setup Kubernetes Cluster
  hosts: all
  become: true
  roles:
    - k8s-cluster-with-ansible
```

Executing the role to bootstrap kuberntes cluster
```yaml
ansible-playbook -i inventory setup_kubernetes.yml
```