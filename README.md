## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Diagram (IC:\Users\colin\Documents\GitHub\CyberSecurityClass\Images\Homework13.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the access logs and system files.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function         | IP Address | OS    |
|------------|------------------|------------|-------|
| Jump Box   | Gateway          | 10.0.0.4   | Linux |
| Web 1      | backend resource | 10.0.0.5   | Linux |
| Web 2      | backend resource | 10.0.0.6   | Linux |
| Web 3      | backend resource | 10.0.0.7   | Linux |
| Elk Server | logging service  | 10.1.0.4   | Linux |
| Loadbalancer | load balancer  | 40.121.3.234|      |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the loadbalancing machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

      75.168.137.210

Machines within the network can only be accessed by the Jumpbox gateway.

A summary of the access policies in place can be found in the table below.

| Name         | Public | Allowed IP     |   |
|--------------|--------|----------------|---|
| Jumpbox      | no     | 75.168.137.210 |   |
| Web 1        | no     | 10.0.0.4       |   |
| Web 2        | no     | 10.0.0.4       |   |
| Web 3        | no     | 10.0.0.4       |   |
| Elk Server   | no     | 10.0.0.4       |   |
| Loadbalancer | yes    | 75.168.137.210 |   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for quick setup and ensures that everything is setup correctly.

The playbook implements the following tasks:
- installs python
- installs docker
- downloads an elk container for docker and configures it for ports 5601,9200,5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[CyberSecurityClass/Images/elkDocker.png]

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4, 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
  FileBeaet
  Metricbeat

These Beats allow us to collect the following information from each machine:
- FileBeat is used to monitor chages to system settings and files within a system it also sends any system logs. MetricBeat is used to monitor metrics for contrainer's meta stats. Such as CPU usage and the number of containers.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/install-elk.yml.
- Update the hosts file to include the elkserver IP as a seperate group so it only runs the elk setup
- Run the playbook, and navigate to public IP of the elk server to check that the installation worked as expected. Ex. http://13.84.211.152:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
