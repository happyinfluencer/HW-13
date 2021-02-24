# HW-13
# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  -: Enter the playbook file. /etc/ansible/playbookan.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _secure____, in addition to restricting _____ to the network.
- : What aspect of security do load balancers protect? What is the advantage of a jump box?_ Load balancer protects the system/ data from the attacks by shifting the attack traffic. 
Jum box is acting like a seperate computer or station for administrator. The admin logs in to jump box and control all other servers from the jump box. It controls gives easy access to other servers, controls traffic and logs, and manages other servers. 
referrence https://securityboulevard.com/2020/05/why-jump-servers-are-obsolete/

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
-: What does Filebeat watch for?_ Filebeat is a logging agent installed on the machine generating the log files, tailing them, and forwarding the data to either Logstash for more advanced processing
-: What does Metricbeat record?_ Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web 1    |Server    | 10.0.0.5   | Ansible          |
| Web 2    |Server    | 10.0.0.6   |Ansible           |
| ELK vm   |Server    | 10.1.0.4   | Filebeat         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the local_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ 174.100.84.142

Machines within the network can only be accessed by _local machine____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Jump Box, IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | Local VM IP          |
| Web 1    | No                  |   10.0.0.4           |
| Web 2    |       No            |   10.0.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ It saves time. By one script you can control many servers.

The playbook implements the following tasks:
- _: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install pip3
- Install Docker python module
- Command sysctl for more memory
- Download a docker elk container
- Command systemctl to enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _: List the IP addresses of the machines you are monitoring_10.0.05 and 10.0.0.6

We have installed the following Beats on these machines:
- _: Specify which Beats you successfully installed_Filebeat

These Beats allow us to collect the following information from each machine:
- _: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ Filebeat helps you keep the simple things simple by offering a lightweight way to forward and centralize logs and files. Metric beat collects metrics and statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the host file to include IP address of Ansible or ELK
- Run the playbook, and navigate to website to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ /etc/ansible/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_/etc/ansible/host
- _Which URL do you navigate to in order to check that the ELK server is running? www.publicip:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ ansible-playbook filebeat-playbook.yml
