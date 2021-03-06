# Project-1-Deploying-ELK-Stack
The purpose of this project is to create, configure, and deploy a live security solution using ELK Stack.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Red_Team_Network_Diagram](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/146bf3904caf5c60b31359f98fd8abc6a1074c0d/Diagrams/Red_Team_Network_Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [DVWA-playbook.yml](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/d7b613eb75a75bad4212479729ca89dcb41847a6/Ansible/DVWA-playbook.yml)
  - [ELK-playbook.yml](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/d7b613eb75a75bad4212479729ca89dcb41847a6/Ansible/install-ELK.yml)
  - _[filebeat-playbook.yml](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/c7d0772ba554ac981d79c84eca90fda0954ea403/Ansible/filebeat-playbook.yml)_
  - _[metricbeat-playbook.yml](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/af268604b97384657c17e9ff3fce6e6d870fd6e1/Ansible/metricbeat-playbook.yml)_
  

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

Additionally, by routing user requests evenly across a group of servers, load balancers minimize the likelihood of downtime. They do this by rerouting traffic to other servers in the group if one should fail, resluting in eliminating a single point of failure if the network is attacked. 
  
The main advantage of the jump box VM is that it acts as an intermediary between the internet and web machines. Because the Jump box VM is the only machine that connect to the servers it adds an additional layer of protection, restricting communication on  ports that can access the web machines. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log events and system services.
- Filebeat ships log files. It generates log files on the machines it is installed on, tailing them, and then forwarding the data to either Logstash for more advanced processing or directly into Elasticsearch for indexing.
- Metricbeat collects metric data from your target servers that it is installed on. For example, operating system metrics such as CPU or memory or data related to services running on the server. It can also be used to monitor other beats and ELK stack itself.

The configuration details of each machine may be found below.

| Name          | Function   | IP Address | Operating System |
|---------------|------------|------------|------------------|
| Jump Box      | Gateway    | 10.0.0.4   | Ubuntu LTS 20.4  |
| Web-1         | Webserver  | 10.0.0.5   | Ubuntu LTS 20.4  |
| Web-2         | Webserver  | 10.0.0.6   | Ubuntu LTS 20.4  |
| Web-3         | Webserver  | 10.0.0.7   | Ubuntu LTS 20.4  |
| ELK VM        | ELK server | 10.1.0.4   | Ubuntu LTS 20.4  | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 74.85.200.25

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Therefore, only the Jump Box machine is allowed to access the ELK VM. The Jump-Box-Provisioners IP address is as follows:
  - Private IP: 10.0.0.4 / Public IP: 20.185.50.174 

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible   | Allowed IP Addresses |
|---------------|-----------------------|----------------------|
| Jump Box      | Yes                   |  74.85.200.25        |
| Web-1         |  No                   |  10.0.0.4            |
| Web-2         |  No                   |  10.0.0.4            |
| Web-3         |  No                   |  10.0.0.4            |
| ELK VM        |  No                   |  10.0.0.4            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because admins can utilize YAML playbooks to run services and trigger updates or reboots on multiple machines faster than doing them individually. The automation frees admins up to focus their time and efforts on more important tasks. 

The playbook implements the following tasks:
- Install docker
- Install python3-pip
- Use pip to install docker
- Increase virtual memory
- Download and launch a docker ELK container
- Enable docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker PS](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/5ab5d32801fcc09c0afe835b83f4238f284b66dc/Images/ELK_VM%20Docker%20PS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5)
- Web-2 (10.0.0.6)
- Web-3 (10.0.0.7)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filbeat is used to collect log files from specific files on remote machines such as files generated by services like Apache  and Microsoft Azure tools, which analysts  can then view in Logstash for more advanced processing or directly into Elasticsearch for indexing.
- Metricbeat collects machine metrics such as CPU and uptime, which analysts can then use to determine how healthy the machine is. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration file to /etc/ansible/files
- For filebeat update the configuration file (filbeat-config.yml) to include the ELK VMs private IP (10.1.0.4) in lines 1106 and 1806.
- For metricbeat update the configuration file (metricbeat-config.yml) to include the ELK VMs private IP (10.1.0.4) in lines 62 and 96.
- Run the playbooks filebeat-playbook.yml and metricbeat-playbook.yml, and navigate to http://104.42.175.47:5601 to check that the installation worked as expected.
- http://104.42.175.47:5601
![Kibana](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/42eda2f24b13ad66dcffe836c07282e62ecd4943/Images/Kibana.png)

- Filebeat
![Filebeat module status](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/efdb48946b2454519d72239b6f211708c67ed21b/Images/filebeat%20module%20status.png)

- Metricbeat
![Metricbeat module status](https://github.com/Hermsd/Project-1-Deploying-ELK-Stack/blob/efdb48946b2454519d72239b6f211708c67ed21b/Images/metricbeat%20module%20status.png)

- The playbooks that were created are DVWA-playbook.yml, ELK-playbook.yml, filebeat-playbook.yml, and metricbeat-playbook.yml were copied to /etc/ansible/roles.
- To make Ansible run the playbook on a specific machine, the hosts file in /etc/ansible/ needs to be updated with groups that have the appropriate machines desired for each group. Then in order to specify the machine you want to install the ELK server on versus to install filebeat and metricbeat, the line for "hosts:" in the filebeat-playbook.yml and metricbeat-playbook.yml must be set to use the webservers group contained in the hosts file and for ELK the "hosts:" in the ELK-playbook.yml must be set to use the ELK group contained in the hosts file.
- In order to check that the ELK server is running navigate to the URL http://104.42.175.47:5601




