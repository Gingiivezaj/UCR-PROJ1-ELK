
The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/Gingiivezaj/UCR-PROJ1-ELK/blob/main/Images/elk%20final%20map.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

 [Filebeat Playbook](https://github.com/Gingiivezaj/UCR-PROJ1-ELK/blob/main/Ansible/filebeat_playbook.txt)

[Metricbeat Playbook](https://github.com/Gingiivezaj/UCR-PROJ1-ELK/blob/main/Ansible/Metricbeat_Playbook.txt)

[Install VM with Docker](https://github.com/Gingiivezaj/UCR-PROJ1-ELK/blob/main/Ansible/Install_Docker_Playbook.txt)

[Install Elk Playbook](https://github.com/Gingiivezaj/UCR-PROJ1-ELK/blob/main/Ansible/Install_Elk_Playbook.txt)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to limiting the exposure of the backend servers directly to the network.
Load Balancers contribute to the Availability aspect of the CIA Triad.
JumpBox is used for System Administration and secured external network access.
The advantage of using a Jumpbox is that it's the originating point for launching Administrative Tasks. This sets the Jumpbox as a Secure Admin Workstation. Anytime administrators want to conduct management tasks they will be required to connect to the Jumpbox. The JumpBox is also configured for restrictive access providing a more secure network environment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the filesystem and system resources.
-  Filebeat watches for either log files or locations that have been configured, while collecting log events and forwarding them to Elasticsearch or Logstash for indexing.
-  Metricbeat records metric and statistical data from the operating system and from the services running the host servers.

The configuration details of each machine may be found below.

![chart 1](https://user-images.githubusercontent.com/94089551/158733408-7f195d86-2583-4132-a2bd-05303588bf07.PNG)


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Whitelisted IP address: Admins personal IP address.


Machines within the network can only be accessed by SSH.
-Which machine did you allow to access your ELK VM? What was its IP address? Jump-Box-Provisioner 10.0.0.4

A summary of the access policies in place can be found in the table below.

![Chart 2](https://user-images.githubusercontent.com/94089551/158733469-1e890f1b-4325-4f02-a130-8193800a4a18.PNG)


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The main advantage that Ansible brings is the automation and simplification of repetitive, complex, and tedious tasks to the System admin. 

The playbook implements the following tasks:
Install: docker.io
Install python3-pip
Install docker module
Increase Memory Use: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Capture](https://user-images.githubusercontent.com/94089551/158733490-84331a28-c6ea-4bd4-89a4-12ddb407cb6b.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines: 

![chart 3](https://user-images.githubusercontent.com/94089551/158733605-1b05c90c-6b43-4d4d-b01f-d2e4c6f8fdc1.PNG)


We have installed the following Beats on these machines:
-Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

 -  Filebeat is a lightweight shipper for forwarding and centralizing log data. Filebeat also monitors log files or locations you specify, collects the log events, and forwards them to either Elasticsearch or Logstash for indexing.

-Metricbeat collects metrics from the operating system and from services running on the server. Metricbeat then takes the metric that it collects and sends them to the output that is specified.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Install_filebeat_Playbook.yml file to the /etc/ansible/files directory. 
- Update the configuration file to include the private IP “10.1.0.4” of the ELK-Server to the ElasticSearch and Kibana sections of the configuration file. 
- Run the playbook, and navigate to http://40.122.169.208:5601/app/kibana to check that the installation worked as expected.
 Create a new playbook in the /etc/ansible/roles directory. This playbook should install, deploy the updated configuration file, enable and configure the system module, run the filebeat setup, and start the filebeat service.
