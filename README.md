#### AUTOMATED-ELK-STACK-DEPLOYMENT-PROJECT

The files in this repository were used to configure the network depicted below.

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Network%20security%20diagram%20-%20Azure%20Resource%20Group.pdf">Azure Resource Group Network Diagram</a>
  
*These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Project 1 Red-Team Network Diagram file may be used to install only certain pieces of it, such as Filebeat

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/install-elk.yml">Elk Instalation Playbook</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/filebeat-playbook2.yml">Filebeat Playbook</a>

<a href="https://github.com/Nathanialuc5019/Project-1/blob/main/Ansible/ansible/files/filebeat-config.yml">Filebeat Configuration</a>



### This ReadMe document contains the following details:
- Description of the Azure Topology
- Screen shot of NSG to displays:  Access Policies
- ELK Configuration
  - Screen shots YML Beats in Use
  - Screen shots Kibana : Machines Being Monitored
- Decription on how to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.


Discuss: What aspect of security do what is load balancers and what does it  protect? What is the advantage of a jump box?_
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.


TODO: What does Filebeat watch for?_
TODO: What does Metricbeat record?_

The configuration details of each machine is found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box-VM | Gateway  |52.249.198.163 (Public) / 10.0.0.5 (Private) | Linux |
| WEB-3 (ELK VM)   | Server   |13.66.210.220 (Public) / 10.2.0.4 (Private | Linux |
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

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because that and automated process can same time, help to recude error and bugs in the deployement and susing infrastructre as code help to keep images to the machines as a sigle script. 

One main advantage to of 

The playbook implements the following tasks:

- SSH into the Jump-Box-VM (ssh redadmin@52.249.198.163)
- Start and then Attached to the ansible docker (sudo docker start frosty_jackson )/(sudo docker attach frosty_jackson)
- Went to /etc/ansible/roles directory and created the ELK playbook (Elk_Playbook.yml)
- Ran the Elk_Playbook.yml in that same directory (ansible-playbook Elk_Playbook.yml)
- SSH into the ELK-VM to verify the server is up and running.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)


### Target Machines & Beats

This ELK server is configured to monitor the following machines:
TODO: List the IP addresses of the machines you are monitoring
We have installed the following Beats on these machines:
TODO: Specify which Beats you successfully installed
These Beats allow us to collect the following information from each machine:
TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.


### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned,
SSH into the control node and follow the steps below:

FILEBEAT
- Copy the filebeat-configuration.yml file to etc/ansible/roles/files.
- Update the filebeal-configuration.yml file to include the ELK private IP  in Lines 1106 and 1806
- Run the playbook, and navigate to http-------- to check that the installation worked as expected.

METRICBEAT
- Copy the metricbeat-configuration.yml file to /etc/ansible/roles/files.
- Update the metricbeat-configuration.yml file to include the ELK private IP in lines 62 and 96.
- Run the playbook, and navigate to http://13.66.210.220:5601/app/kibana (ELK-VM public IP) to check that the installation worked as expected.


TODO: Answer the following questions to fill in the blanks:_
Which file is the playbook? Where do you copy it?_
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
Which URL do you navigate to in order to check that the ELK server is running?
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
roject-1
