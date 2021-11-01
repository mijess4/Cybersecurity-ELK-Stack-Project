## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/87951718/139744035-d017c3b4-98d5-46ce-9bde-7d45463812ac.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  [Install Filebeat](https://github.com/mijess4/Cybersecurity-ELK-Stack-Project/blob/main/ansible/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers sit between the clients and servers providing additional layers of security and enhancing performance. Load balancers intelligently distribute incoming traffic among the servers while also detecting and droping Distributed Denial-of-Service (DDoS) attacks before it gets to the website; thus ensuring availability.
  A jump box offers the benefit of secure remote access to the network as it set up with very resticted access and no returning Internet access for any protocol. The jump box has a single purpose as an SSH gateway, only one path in via SSH which requires a key; this drastically reduces chances of a brute force attack. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.
- Filebeat monitors the log files or specifed locatins, collects log events, and forwads them to Elasticsearch or Logstash for indexing.
- Metricbeat periodically collect metrics from the system and services running on the server and ships them to the desired output, such as Elasticsearch or Logstash. 

The configuration details of each machine may be found below.

|         Name         	|  Function 	| IP Address 	|  Operating System  	|
|:--------------------:	|:---------:	|:----------:	|:------------------:	|
| Jump-Box-Provisioner 	| Gateway   	| 10.0.0.4   	| Linux Ubuntu 18.04 	|
| Web-1                	| Webserver 	| 10.0.0.5   	| Linux Ubuntu 18.04 	|
| Web-2                	| Webserver 	| 10.0.0.7   	| Linux Ubuntu 18.04 	|
| Web-3                	| Webserver 	| 10.0.0.8   	| Linux Ubuntu 18.04 	|
| ELK-SERVER           	| Elk-Stack 	| 10.1.0.4   	| Linux Ubuntu 18.04 	|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box virtual machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.87.136.234

Machines within the network can only be accessed by The Jump Box Provisioner.
- 13.92.180.58

A summary of the access policies in place can be found in the table below.

|         Name         	| Publicly Accessible 	| Allowed IP Addresses 	|
|:--------------------:	|:-------------------:	|:--------------------:	|
| Jump-Box-Provisioner 	| No                  	| 73.87.136.234        	|
| Web-1                	| No                  	| 13.92.180.58         	|
| Web-2                	| No                  	| 13.92.180.58         	|
| Web-3                	| No                  	| 13.92.180.58         	|
| ELK-SERVER           	| No                  	| 13.92.180.68        	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for the streamlining of installations, updates, configurations management, deployment and more to a server, as well as the automation of daily tasks.

The playbook implements the following tasks:
- Install docker and python3-pip.
- Install Docker module.
- Increase and use more memory.
- Download and launch a Docker ELK contaainer.
- Enable Docker automatically upon booting the machine.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/87951718/139755712-da6207db-6585-47c6-82db-2295bdfb3119.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.7
- 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- FileBeat will conllect and forward log files and data, such as times and dates of events, to Elasticsearch or Logstash. Metricbeat will do the same for metrics and stats, such as CPU memory. Such data can later be compiled and analyzed using Kibana.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to your Web VMs.
- Update the /etc/annsible/hosts file to include the IP address of the ELK and VM webservers.
- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.
- The playbook file is /etc/ansible/filebeat-config.yml and it is copied to /etc/filebeat/filebeat.yml
- To make ansible run the playbook on a specific machine, update the filebeat-config.yml file. Use the hosts file to update the IP addressess and choose which to run on ansible.
- Navigate to Kibana/logs/DEBtab/, scroll down, and check taht the beat is running.

Use the following useful commands to run filebeat:

- curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml
- curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-darwin-x86_64.tar.gz
- dpkg -i filebeat-7.4.0-amd64.deb
- filebeat modules enable system
- filebeat setup
- service filebeat start

Repeat the process for metricbeat.
