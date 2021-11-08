# ELK-Project
This my a walk through of the ELk Project.


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

['CloudSecurity.drawio.png'](ELK-Project/Images/'CloudSecurity.drawio.png')

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml, metricbeat-playbook.yml, install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers help protect you from Dos attacks. An advantage of having a jumpbox is that it allows you to access and managethe VMs.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- Filebeat watches out for any changes in the files location, it then collects that data and sends it to logstash/elasticsearch. 
- Metricbeat recordes and collects the metric data and sends it to logstash/elasticsearch.

The configuration details of each machine may be found below.


| Name     | Function       | IP Address          | Operating System |
|----------|----------------|---------------------|------------------|
| Jump Box | Gateway        | 52.165.152.16       | Linux            |
| Web-1    | DVWA Container | Pub: 52.465.170.74  | Linux            |
|          |                | Priv: 10.0.0.5      |                  |
| Web-2    | DVWA (backup)  | 10.0.0.9            | Linux            |
| Web-3    | ELK Container  | 10.0.0.10           | Linux            |
| ELK-SERV | ELK Container  | Pub: 104.42.170.177 | Linux            |
|          |                | Priv: 10.1.0.4      |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 10.0.0.0/16

Machines within the network can only be accessed by the Jumpbox.
- The Jumpbox machine (IP: 52.165.152.16) has access to the ELK VM.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.0/16          |
| Web-1    | No                  |                      |
| Web-2    | No                  |                      |
| Web-3    | No                  |                      |
| ELK-SERV | No                  | 104.42.170.177       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The ansible playbook could be utalized instead of manually configuring each machine.

The playbook implements the following tasks:
- Install docker.io
- Install PIP
- Install docker python module
- Download and install the docker ELK Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[ELK-Project](Images/docker_ps_output.png)        

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (IP: 10.0.0.5)

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- We are working with two types of beats in this project, Filebeat and Metricbeat. Filebeat permits the ELK Server to monitor all users who accessed any files. This tool is extremely valuable because it keeps track of when files are accessed or modified. Metricbeat permits the ELK Server to collect metrics, as in memory usage, CPU usage, and what goes in and out of a server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml and metricbeat-playbook.yml files to /etc/ansible/roles.
- Update the /etc/ansible/hosts file to include the IP address of the machine under webserver.
- Run the playbook, and navigate to http://52.165.170.74:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it?  The playbbook is a .yml file. It is coppied into a computer.
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? The host file allows the VMs to be in a group so the playbooks can be deployed.
- Which URL do you navigate to in order to check that the ELK server is running? Use http://104.42.170.177:5601/app/kibana to ensure that the ELK-Server is running.

### Project Documentation
These are some of the notes that I took throughout the ELK Project.

Day 1:
[README.zip](Images/'Project_ Day 1-page-001.jpg') 


Day2:
[README.zip](Images/'Project_ Day 1-page-001.jpg')
[README.zip](Images/'Project_ Day 1-page-002.jpg') 

