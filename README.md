
# OCI IAM Automation with Ansible

## Description
This project involves automating the creation and management of users, groups, and policies (IAM) in Oracle Cloud Infrastructure (OCI) using Ansible. The automation process uses Ansible playbooks to create the necessary IAM components, ensuring consistent and efficient management of resources within OCI. The compartments `resourcesNetworking`, `resourcesCompute`, and `resourcesDatabase` must be pre-configured.

# Video Walkthrough: 
[![Watch the Video](https://img.youtube.com/vi/7yTiAR2RiAE/0.jpg)](https://www.youtube.com/watch?v=7yTiAR2RiAE)

## Create Compartments with Oracle Cloud CLI
  ```bash 
  # Create resourcesNetworking compartment
  oci iam compartment create --name resourcesNetworking --description "Compartment for Networking resources" --compartment-id <parent-compartment-id>

   # Create resourcesCompute compartment
  oci iam compartment create --name resourcesCompute --description "Compartment for Compute resources" --compartment-id <parent-compartment-id>
  
  # Create resourcesDatabase compartment
  oci iam compartment create --name resourcesDatabase --description "Compartment for Database resources" --compartment-id <parent-compartment-id>

  ```

## Setup and Execution Steps

1. **Setting up the environment variable**
   - Retrieve and replace the OCID of the Tenancy and the compartments: `resourcesNetworking`, `resourcesCompute`, and `resourcesDatabase`:
     ```bash
     export PARENT_COMPARTMENT_OCID=<insert-TENANCY-ocid>
     export NETWORKING_COMPARTMENT_OCID=<insert-NETWORKING_COMPARTMENT-ocid>
     export COMPUTE_COMPARTMENT_OCID=<insert-COMPUTE_COMPARTMENT-ocid>
     export DB_COMPARTMENT_OCID=<insert-DB_COMPARTMENT-ocid>
     ```

2. **Creating and accessing a folder to download the code**
   ```bash
   mkdir tcb-bmc-iam
   cd tcb-bmc-iam
   ```

3. **Downloading the file Ansible Playbooks**
   ```bash
   wget https://objectstorage.us-ashburn-1.oraclecloud.com/p/eRJ8pKclDBA_MZeuAqj75jkfPq3yvuqe4TslzNjqY7Y1RKTLMGipnbwfPO7cnp5F/n/idqfa2z2mift/b/bootcamp-oci/o/EN/oci-handson-module-iam.zip
   unzip oci-handson-module-iam.zip
   ```

4. **Running the Ansible Playbooks from Cloud Shell**
   ```bash
   ansible-playbook tcb-bmc-iam-creating-groups-and-policies.yaml
   ansible-playbook tcb-bmc-iam-creating-users-cloud-admin.yaml
   ansible-playbook tcb-bmc-iam-creating-users-dba-admin.yaml
   ansible-playbook tcb-bmc-iam-creating-users-network-admin.yaml
   ansible-playbook tcb-bmc-iam-creating-users-compute-admin.yaml
   ansible-playbook tcb-bmc-iam-creating-users-operators.yaml
   ```

## What I Learned

Through this project, I gained valuable experience in automating IAM tasks in Oracle Cloud Infrastructure using Ansible. Specifically, I learned how to:

- Set up and configure environment variables for OCI.
- Download and manage Ansible playbooks from Cloud Shell.
- Automate the creation of users, groups, and policies in OCI, which streamlines administrative tasks and ensures consistency across resources.
