# RonaldSenoren-Project-1
Ronald Senoren's Project 1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/rsenoren/RonaldSenoren-Project-1/blob/c90e7a93e6eb0619fa9d839605513741089ce195/Diagrams/RONALD%20RESOURCE%20GROUP%20DIAGRAM.drawio.png)
RonaldSenoren-Project-1/Diagrams/RONALD RESOURCE GROUP DIAGRAM.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - RonaldSenoren-Project-1/Scripts/Ansible/Filebeat_Playbook/Filebeat_Playbook.yml
  
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
        Load balancers help prevent DDoS attacks. Jumpboxes have access to each system but connects to one node for easier monitoring.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_ monitors log files to collect log events
- _TODO: What does Metricbeat record?_ records the metrics and statistics from the operation system and services running on a server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |40.118.254.86| Linux           |
| WEB 1    | Server   | 10.0.0.7   | Linux            |
| WEB 2    | Server   | 10.0.0.8   | Linux            |
| ELK      | ELK SERV | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 98.47.6.19 (MY PC)

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
         Jumpbox: 40.118.254.86

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |  98.47.6.19          |
| WEB 1    | NO                  |  40.118.254.86       |
| WEB 2    | NO                  |  40.118.254.86       |
| ELK      | No   PORT:5601      |  40.118.254.86       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
         Automating configuration with Ansible could help save a lot of time. Without Ansible, automation could be very time consuming.
         
The playbook implements the following tasks:
-  TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-     Install Docker
-     Install Python-pip
-     Install docker python module
-     Set the vm.max_map_count to 262144
-     Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/rsenoren/RonaldSenoren-Project-1/blob/c90e7a93e6eb0619fa9d839605513741089ce195/Images/DOCKER_PS.png)
RonaldSenoren-Project-1/Images/DOCKER_PS.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
-        WEB 1: 10.0.0.7
-        WEB 2: 10.0.0.8

We have installed the following Beats on these machines:
-        Filebeat
-        Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to /etc/ansible.
- Update the hosts file to include the Elk Server IP address of 10.3.0.4 under elkservers.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected..

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
-     ELK_SERVER_INSTALL.yml; Ansible container folder /etc/ansible/files/
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
-     /etc/ansible/; Update "hosts" files and add new webserver group "elk" then add Elk IP to new webserver group  
- _Which URL do you navigate to in order to check that the ELK server is running?
-     20.109.18.79:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
