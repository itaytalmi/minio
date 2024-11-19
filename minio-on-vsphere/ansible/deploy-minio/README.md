# Deploying MinIO on vSphere
- [Deploying MinIO on vSphere](#deploying-minio-on-vsphere)
  - [Ansible Playbook Usage](#ansible-playbook-usage)

This directory contains Ansible code that can be used to automatically deploy and configure MinIO on vSphere.

It currently performs the following:

- Retrieves the Ubuntu Cloud Image OVA and deploys it to vSphere
- Generates Cloud-Init config for the deployed machine
- Configures the deployed machine with additional resources (CPU, Memory, Disks)
- Configures an additional filesystem for the MinIO data directory
- Installs and configures MinIO

## Ansible Playbook Usage

Install the required Python modules using the `requirements.txt` file.

```bash
pip3 install -r requirements.txt
```

Install the required Ansible collection using the `requirements.yml` file.

```bash
ansible-galaxy install -r requirements.yml
```

Update the `vars.yml` file using your configuration.

>See the Ansible roles in the sub-directories for additional parameters you can override.

To execute the Playbook:

```bash
ansible-playbook playbook.yml
```

>If you need to redeploy the MinIO VM, set `redeploy_vm` to `true`. **Important note**: this will destroy the existing machine, so make sure you backup any relevant data and use this variable with extra caution!

```bash
ansible-playbook playbook.yml -e redeploy_vm=true
```
