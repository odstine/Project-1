# Project-1
ELK Stack, Syntax, and Diagrams

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Stine,O_Hw_Diagram 1a.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Diagram file may be used to install only certain pieces of it, such as Filebeat.

  - my-playbook.yml
  - metricbeat-playbook.yml
  - filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and redundant systems in place, in addition to restricting outside exposure to the network.
_ The jump box is the only access point to get to the load balancer and VMs in the network. The security group limits who can enter the network, which has been limited to one device.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system protocols.
- Filebeat monitors the logs, collects information and forwards them on to the ELK stack.
- Metricbeat takes the metrics and stats that is collected and deploys the information to a location of the users choice.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | DVWA     | 10.0.0.6   | Linux            |
| Web-2    | DVWA     | 10.0.0.7   | Linux            |
| ELK-SERV | Ext. Loc | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 107.77.214.194

Machines within the network can only be accessed by Jump-Box.
- Web-1 (10.0.0.6)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4/16          |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The advantage of having Ansible automatically configured is that it will turn on and run automatically with each VM that is turned on.

The playbook implements the following tasks:

- Install Docker
- Install pip3
- Install Docker python module
- Allow for memory use
- Download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/sudo_docker_syntax.jpg)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.1 
- 10.0.0.6 
- 10.0.0.7 
- 10.1.0.4

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the logs, collects information and forwards them on to the ELK stack.
- Metricbeat takes the metrics and stats that is collected and deploys the information to a location of the users choice.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to the ansible container.
- Update the config file to include proper IP addresses and ports
- Run the playbook, and navigate to filebeat-playbook to check that the installation worked as expected.

You specify IP addresses for the VMs that you want filebeat & metricbeat to run on in the config file. Then you will need to specify the ports, like 5601 for Kibana, so that the information is being directed to an area of the users specification.
