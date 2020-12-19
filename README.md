## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](Berkeley-Course/Diagram/Network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk Deployment] (./Ansible/Elk_VM_Setup.yml)
  - [Filebeat Deployment] (./Ansible/Filebeat.yml)
  - [Metricbeat Deployment] (./Ansible/Metricbeat.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stability, in addition to restricting traffic to the network.
What aspect of security do load balancers protect? A Load Balancer will provide redundancy to a network to ensure stability within a network. What is the advantage of a jump box? A jump-box allows a secure connection into a network to assist with setting up additional systems on the network._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-Filebeat monitors the log files
-Metricbeat records the statistics and metrics of the OS and running services

The configuration details of each machine may be found below.
| Name     	| Function       	| IP Address 	| OS    	|
|----------	|----------------	|------------	|-------	|
| Jump-Box 	| Gateway        	| 10.0.0.1   	| Linux 	|
| Web-2    	| DVWA Container 	| 10.0.0.10  	| Linux 	|
| Web-3    	| DVWA Container 	| 10.0.0.7   	| Linux 	|
| Web-4    	| DVWA Container 	| 10.0.0.8   	| Linux

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-76.169.194.114

Machines within the network can only be accessed by ssh.
- The ELK VM allows access from the Jump Box machine.    Ip:10.0.0.4 is whitelisted

A summary of the access policies in place can be found in the table below.

| Name          | Public Accessible| Allowed IP's   	|
|---------------|------------------|----------------	|
| Jump-Box      | Yes              | 76.169.194.114 	|
| Load-Balancer | Yes              | 76.169.194.114 	|
| ELK Server    | Yes              | 76.169.194.114  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-It allows uniform setups of multiple machines across the network, enabling quicker set up rather than building each machine individually.

The playbook implements the following tasks:
- Step 1: Installs Docker.io
- Step 2: Installs Python3-pip
- Step 3: Installs Docker Module
- Step 4: Increases Memory aloowance
- Step 5: Download and Launches a Docker Elk Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps result](Berkeley-Course/Diagrams/ELK-PS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-2: 10.0.0.10
- Web-3: 10.0.0.7
- Web-4: 10.0.0.8

We have installed the following Beats on these machines:
- Filebeats and Metricbeats are installed on the virtual machines.

These Beats allow us to collect the following information from each machine:
-Filebeat monitors the log files.
-Metricbeat records the statistics and metrics of the OS and running services

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YML file to the ansible directory.
- Update the hosts file to include host IP.
- Run the playbook, and navigate to http://<machine_IP>:5601 to check that the installation worked as expected.
