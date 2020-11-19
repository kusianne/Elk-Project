### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Elkcloud.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ___yml__ file may be used to install only certain pieces of it, such as Filebeat.

Filebeat-playbook.yml.

This document contains the following details:

-Description of the Topology
-Access Policies
-ELK Configuration
-Beats in Use
-Machines Being Monitored
-How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly __available___, in addition to restricting __access___ to the network.

Load balancers are a huge part in defending organizations against distributed denial of service(DDoS). 

The advantage of a jump box is that it keeps access to the network and virtual machines secure.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __files___ and system __metrics___.

Filebeat forward and centralize log data, in addition Filebeat monitors the log files or locations that are specified, it collects log events and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat collects metrics from the operating system and from services running on the server. It takes the metrics and statistics that are collected and ships them to the output that is specified, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |10.0.0.4    | Linux            |
| Web1     | Webserver|10.0.0.5    | Linux            |                  
| Web2     | Webserver|10.0.0.6    | Linux            |
| Web3     | Webserver|10.0.0.7    | Linux            |
| Web4     | Elkserver|10.2.0.4    | Linux            |
 
### Access Policies

The machines on the internal network are not exposed to the public Internet.
Only the __Jumpbox___ machine can accept connections from the Internet. Access to this machine is only allowed from my local host IP address.

Machines within the network can only be accessed by Jumpbox IP Address:20.55.0.160 and the Load balancer IP Address: __52.142.44.30___.

I allowed the Jump box IP address to access the Elk VM with the Jump box public IP address 20.55.0.160

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Local host IP        |
| web1     | Yes                 | 52.142.44.30         |
| Web2     | Yes                 | 52.142.44.30         |
| Web3     | Yes                 | 52.142.44.30         |
| Web4     | Yes                 | Any Ip on the web    |
|                                 through the security  |
|                                 group                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it reduces errors.

The main advantage of automating configuration with Ansible is that it is faster and consistent in running the scripts and leave room to do more work.

The playbook implements the following tasks:

The ELK installation playbook install: 
... Docker.io
... Python3-pip
... Download and launch a docker elk container

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Diagrams/docker_ps_elk761.PNG

### Target Machines & Beats

This ELK server is configured to monitor the following machines: Web1 Web2 and Web3

The IP addresses of the machines that are being monitored: 
Web1 IP Address: 10.0.0.5 
Web2 IP Address: 10.0.0.6 
Web3 IP Address: 10.0.0.7

We have installed the following Beats on these machines:

Successfully installed Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat collects log files, which we use to collect log events.
Metricbeat collects metrics from the operating system and from services running on the server, which helps us monitor and analyze system CPU, memory and load

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the __install-Elk.yml___ file to __/etc/ansible/___.
Update the __hosts___ file to include the Elk private Ip address
Run the playbook, and navigate to _the Elk VM___ to check that the installation worked as expected.

The playbook is a Yaml file to be copied to the /etc/ansible/ directory.
The hosts file needs to be updated to make Ansible run the playbook on a specific machine. We need to add the private IP under "servers" to specify which machine to install the ELK server on versus which to install Filebeat on.
In order to check that the ELK server is running, navigate to `http://<13.86.115.130>:5601/app/kibana`


