## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Ubuntu 18.04 LTS |
| DVWA-01  | DVWA VM  | 10.0.0.5   | Ubuntu 18.04 LTS |
| ELKS-01  | ELK Stack| 10.0.0.6   | Ubuntu 18.04 LTS |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  - 70.48.74.0/24

Machines within the network can only be accessed through the Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 70.48.74.0/24        |
| DVWA-01  | No                  | 10.0.0.4             |
| ELKS-01  | No                  | 70.48.74.0/24        |
|          |                     | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible uses preconfigured setup files which can be carried over and deployed on other systems without having to enter them. This is known in Ansible as a playbook.

The playbook implements the following tasks:
  - Install Docker and the Docker python module
  - Install python
  - Install Docker ELK container


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  - 10.0.0.5: DVWA-01

We have installed the following Beats on these machines:
  - DVWA-01: Filebeat, Metricbeat

These Beats allow us to collect the following information from each machine:
  - Filebeat collects log data from the system and forwards it to Elasticsearch.
  - Metricbeat collects system performance data and forwards it to Elasticsearch.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_ELK.yml file to /etc/ansible/playbooks.
- Update the /etc/ansible/hosts file to include the internal IP address of the machines that the playbook will be installed on.
- Run the playbook, and navigate to the ELK server's public IP and port 5601 to check that the installation worked as expected.
