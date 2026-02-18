# Lab Wk 7 
by Kyle, Cole, and Jessica

# Intro to Ansible Lab

## Commands We Used

### SSH Key Management
```bash
# Create a new SSH key pair named "aws" and add it to ~/.ssh
ssh-keygen -t rsa -b 2048 -f ~/.ssh/aws

# Import the new key to AWS
./scripts/import_lab_key ~/.ssh/aws.pub

# Remove the SSH key from AWS when done
./scripts/delete_lab_key aws
```

These commands let us securely access our AWS EC2 instances.
