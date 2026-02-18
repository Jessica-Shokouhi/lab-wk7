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

* **Initialize Terraform**:

```bash
terraform init
```

* **Format Terraform files**:

```bash
terraform fmt
```

* **Validate Terraform configuration**:

```bash
terraform validate
```

* **Plan Terraform deployment**:

```bash
terraform plan
```

* **Apply Terraform configuration to create resources**:

```bash
terraform apply
```

* **Destroy Terraform resources after lab completion**:

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
<img width="1137" height="951" alt="image" src="https://github.com/user-attachments/assets/3fed45ed-91af-460c-a8bb-b8a78d67b2aa" />



---

## Notes

* We used the public IP or DNS from Terraform output to populate `hosts.yml` for static inventory.
* All modules in the playbook use the fully qualified collection name (FQCN).
* Nginx service is enabled and reloaded to ensure the configuration is active.



