# Sample Portworx ansible playbook

## Overview
This is a sample ansible playbook to deploy Portworx in a **disaggregated** architecture.
Portworx storage nodes are deployed as standalone docker in at least 3 servers (highly recommended) and then deploys Portworx as storageless nodes on an Openshift 3.11 cluster.

For more details on the disaggregated architecture please see the documentation [here](https://docs.portworx.com/cloud-references/deployment-arch/).

## Pre-requisites

### ETCD database 
An external ETCD database cluster must be available so Portworx can be deployed in a disaggregated architecture.

### Storage nodes
All storage nodes are expected to meet minimal Portworx prerequisites as defined [here](https://docs.portworx.com/start-here-installation/).

Also the following software is expected to be installed on each server:
* python 2.7.x (for Ansible)
* docker 

Each server must also have available storage for Portworx to consume.

### Openshift cluster
Portworx will be automatically installed as *storageless* nodes in the Openshift cluster and will join the Portworx storage nodes deployed in the standalone servers.

This ansible was tested with Openshift 3.11 only. 

## Running the ansible playbooks
## Update variables
First update all variables to match your environment in the file *group_vars/all*.

## Update hosts
Update *hosts* file to your environment.

## Update the site file
Also update the *site.yaml* file, specifically the user you want ansible to use.

## Run the playbook
```
ansible-playbook -i hosts test.yaml
```
