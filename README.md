## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.
(Images/Elk_Diagram.jpg)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible-config.yml file may be used to install only certain pieces of it, such as Filebeat.
This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available in addition to restricting attacks to the network.
Load balancers ensure uptime if one server needs to be updated or such, and a jump box allows secure connections via ssh. 
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
What does Filebeat watch for? It watches for log files, collects log events, and forwards it all to the Elasticsearch or Logstash. 
What does Metricbeat record? It records metrics and stats that are collected.
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name     | Function | IP Address |        Operating System |
|----------|----------|------------|         ------------------
|Jump Box | Gateway  |  10.0.0.1   |             Linux            
|Elk      |Elk Server   10.2.0.4/20.98.87.130 |  Linux                |Web 1    |Web Server   10.0.0.10                Linux                 
|Web 2    |Web Server     10.0.0.9                 Linux                 |

Workstation |Access control| |Public IP|         Linux
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.207.173.116 Machines within the network can only be accessed by the Jumpbox and workstation.
Which machine did you allow to access your ELK VM? What was its IP address?_ Jump-Box-Provisioner IP: 10.0.0.1 and the workstation with its public ip. 
A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| JumpBox  |No| The workstation’s public ip on port 22  |
| Elk   | No|The workstation’s public ip on port 5601 
| Web 1 | No|10.2.0.4 on port 22
| Web 2 |      No  10.2.0.4 on port 22
| Load Balancer |No|The workstation’s public ip on port 80

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage of automating configurations with ansible is that you don’t have to manually write new code every time you want to complete the same tasks you’ve already specified for.
The playbook implements the following tasks:
- It installs docker.io, pip3, and the Docker python module
- It allows more memory to be used
- It downloads and starts an elk container
- It enables service docker while booted
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps.jpg)
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.7
10.0.0.9
10.0.0.10
We have installed the following Beats on these machines: Elasticsearch and Kibana
These Beats allow us to collect the following information from each machine: Elasticsearch takes data and then stores it by rules set by the user, and then that data becomes searchable, allowing the user to analyze it in real time. Kibana lets us analyze large amounts of logs and then displays them in graphics that are easy to comprehend.  
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the filebeat config file to etc/ansible/filebeat-config.yml
- Update the filebeat config file to include your specific ELK server's IP address
- Run the playbook, and navigate to the Filebeat installation page to check that the installation worked as expected.
- _Which file is the playbook? Where do you copy it?_ filebeat-playbook.yml; /etc/ansible/filebeat-config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? /etc/filebeat/filebeat-config.yml
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ By editing the filebeat-config.yml file
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.VM.IP]:5601/app/kibana





