#### AUTOMATED-ELK-STACK-DEPLOYMENT-PROJECT

The files in this repository were used to configure the network depicted below.

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Network%20security%20diagram%20-%20Azure%20Resource%20Group.pdf">Azure Resource Group Network Diagram</a>
  
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Project 1 Red-Team Network Diagram file may be used to install only certain pieces of it, such as Filebeat

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/install-elk.yml">Elk Instalation Playbook</a>


### This ReadMe document contains the following details:
- Description of the Azure Topology
- Screen shot of NSG to displays:  Access Policies
- ELK Configuration
  - Screen shots YML Beats in Use
  - Screen shots Kibana : Machines Being Monitored
- Decription on how to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting inbound traffic to the network.

The load balancer aids in security by offloading traffic from a corporate server to a public cloud provider. Integrating an ELK (Elasticsearch, Logstash, and Kibana) server allows users to easily monitor the vulnerable VMs for changes to the file names and watch system metrics.

Filebeat monitors the logs in the specified locations. It detects changes to the filesystem. It collects logs and forwards them to Elastisearch or Logstash for indexing

Metricbeat detects changes in system metrics such as CPU usage. We use it to detect SSH login attempts

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the netwok and system logs.


The configuration details of each machine is found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box-VM | Gateway  |52.249.198.163 (Public) / 10.0.0.5 (Private) | Linux |
| WEB-3 (ELK VM)   | Server   |13.66.210.220 (Public) / 10.2.0.4 (Private) | Linux |
| WEB-1 VM     | Server   |10.0.0.5 (Private)   | Linux            |
| WEB-2 VM     | Server   |10.0.0.9 (Private)            | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. Only the Jump-Box-VM machine can accept connections from the Internet. 
Access to this machine is only allowed from the following IP addresses:
  75.3.88.234 (LocalHost IPaddress)

*Machines within the network can only be accessed by the Jump-Box-VM.

The only machine allowed to access the WEB-3 (ELK VM) is the Jump-Box-VM from 10.0.0.4 Private IP

A summary of the access policies in placed is in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box-VM | Yes             | 75.3.88.234   |
| WEB-3 (ELK VM)         |No    |  10.0.0.4                    |
| WEB-1 VM         |No          | 10.0.0.4                     
| WEB-2 VM         |No         | 10.0.0.4                  |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because using an automated process can save time, help to recude error and bugs in the deployement and susing infrastructre as code isure uniformaty of the imgages and help to keep images to the machines as a sigle script. 

One main advantage to of 

The playbook implements the following tasks:

- Install docker on all network machines so they will be able to recieve and install containers
- Ansible is installed on the Jump Box VM to distribute containers to other VMs on the network
- Ansible playbooks are used to install the ELK stack container on the ELK server and a 'Beats' containers on the Web servers

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Images_Elk%20Stack%20Deployment%20Project/Docker%20ps%20screenshot.PNG">Installed Docker Image</a>

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

| Name     | IP Addresses |
|----------|---------------------|
| WEB-1 VM         | 10.0.0.5  |                   
| WEB-2 VM           | 10.0.0.9 |

I have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat - Filebeat detects changes to the filesystem. We are using this to monitor our Web Log data.
- Metricbeat - Metricbeat detects changes in system metrics, such as CPU usage. We use it to detect SSH login attempts, failed sudo escalations, and CPU/RAM statistics.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned,
SSH into the control node and follow the steps below:

FILEBEAT

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/filebeat-playbook2.yml">Filebeat Playbook</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/files/filebeat-config.yml">Filebeat Configuration</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Images_Elk%20Stack%20Deployment%20Project/filebeat.screenshot.PNG">Filebeat Syslog Dashboard</a>

- Copy the filebeat-configuration.yml file to /etc/ansible directory.
- Update the filebeat-configuration.yml file to include the ELK private IP.
- Run the playbook, and navigate to http://13.66.210.220/ (ELK-VM public IP) to check that the installation worked as expected

METRICBEAT

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/metricbeat-playbook.yml">Metribeat Playbook</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/metrics/metricbeat-config.yml">Metribeat Configuration</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Images_Elk%20Stack%20Deployment%20Project/metricbeat.screenshot.PNG">Host Overview Dashboard</a>

- Copy the metricbeat-configuration.yml file to /etc/ansible directory.
- Update the metricbeat-configuration.yml file to include the ELK private IP.
- Run the playbook 
--cd /etc/ansible
-- ansible-playbook elk-playbook.yml
-- ansible-playbook filebeat-playbook2.yml
-- ansible-playbook metricbeat-playbook.yml
- Navigate to http://13.66.210.220:5601/app/kibana (ELK-VM public IP) to check that the installation worked as expected.
