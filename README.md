# Lab Wk 7 
by Kyle, Cole, and Jessica

# Working with Ansible


## Overview
For this lab, we set up two EC2 instances using Terraform and configured them as Nginx web servers using Ansible. We installed Nginx, added a custom configuration file, created a directory for the web page, deployed an `index.html` template, and ensured the Nginx service was enabled and running.

---

## Commands

### SSH Key Management
- **Create a new SSH key pair named `aws`**:
```bash
ssh-keygen -t rsa -b 2048 -f ~/.ssh/aws
````

* **Import the public key to AWS using the provided script**:

```bash
./scripts/import_lab_key ~/.ssh/aws.pub
```

* **Delete the SSH key when done**:

```bash
./scripts/delete_lab_key aws
```

### Terraform Commands

* **Initialize Terraform and download required providers**:

```bash
terraform init
```

* **Format Terraform files for readability**:

```bash
terraform fmt
```

* **Validate the Terraform configuration for errors**:

```bash
terraform validate
```

* **Preview the changes Terraform will make**:

```bash
terraform plan
```

* **Apply the configuration to create EC2 instances**:

```bash
terraform apply
```

* **Remove all resources created by Terraform**:

```bash
terraform destroy
```

### Ansible Commands

* **Check playbook syntax**:

```bash
ansible-playbook -i inventory/hosts.yml playbook.yml --syntax-check
```

* **Run playbook**:

```bash
ansible-playbook -i inventory/hosts.yml playbook.yml
```

* **Test connection to all hosts**:

```bash
ansible all -i inventory/hosts.yml -m ping
```

---


## Screenshot

<img width="1169" height="923" alt="image" src="https://github.com/user-attachments/assets/4a03f5d6-63af-4e9a-8e70-866b6e284592" />

## Repository Structure (after running ls -R)
#### ansible/
- ansible.cfg
- playbook.yml
- terraform.tfstate
- files/
- inventory/
- playbooks/
- templates/
#### ansible/files/
- index.html
- nginx.conf
#### ansible/inventory/
- hosts.yml
#### ansible/playbooks/
- webserver.yml
#### ansible/templates/
- index.html.j2
#### scripts/
- delete_lab_key
- import_lab_key
#### terraform/
- main.tf
- terraform.tfstate
- terraform.tfstate.backup


## Cleanup

After finishing the lab:

```bash
terraform destroy       # We Remove all EC2 instances
./scripts/delete_lab_key aws   # Remove SSH key from AWS

```
---


## Notes

* We used the public IP or DNS from Terraform output to populate `hosts.yml` for static inventory.
* All modules in the playbook use the fully qualified collection name (FQCN).
* Nginx service is enabled and reloaded to ensure the configuration is active.



