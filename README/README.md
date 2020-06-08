## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/Network_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml and metricbeat-playbook.yml files may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load Balancers protest the availiblity side of the CIA triad by ensuring whatever website or program stays up through balancing the traffic to it. The advantage of a jump box is that youre not using your personal IP address when working and additionaly its a controlled enviroment where you can make changed and tests without messing with your main system.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system interface.
- _TODO: What does Filebeat watch for? Log Files and Log events
- _TODO: What does Metricbeat record? System and Server metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | Ip Address | OS    |
|----------|------------|------------|-------|
| Jump Box | Gateway    | 10.0.0.8   | Linux |
| DMV-VM   | Deployer   | 10.0.0.6   | Linux |
| ELK-VM   | Control VM | 10.0.0.9   | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:72.207.121.70
- _TODO: 72.207.121.70

Machines within the network can only be accessed by DMV-VM.
- _TODO: Which machine did you allow to access your ELK VM? DMV-VM: 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.207.121.70        |
| DMV-VM   | No                  | 10.0.0.8             |
| ELK-VM   | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because we can simply run the playbook to update or start the ElK Machines.
- _TODO: What is the main advantage of automating configuration with Ansible? We can simply run the playbook to update or start the ElK Machines.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- "- name: Install docker.io" is the start of the command to install docker into the Elk server.
- "- name: Install pip" installs python-pip into the Elk server.
- "- name: Install Docker python module" installs the python addon that allows it to work with docker. 
- "- name: Increase virtual memory" increases the virtual memory on the system so everything can function properly
- "- name: download and launch a docker elk container" Downloads a docker and launches it.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: 10.0.0.6, 10.0.0.8, 10.0.0.9

We have installed the following Beats on these machines:
- _TODO: Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects events logs such as a new Ip connecting to an IP. Metricbeat collects metric information from the vms such as cpu usage and ships them to an output for viewing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible folder.
- Update the playbook file to include your hosts information
- Run the playbook, and navigate to [http://machine public ip address:5601] to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? file/metricbeat-playbook.yml Where do you copy it? The ansible Folder
- _Which file do you update to make Ansible run the playbook on a specific machine? You update the Hosts file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? You specify by changing the hosts file to the Ip address of the machine that you want to run. You can also change the host file in the playbook to specify which group to do it on.
- _Which URL do you navigate to in order to check that the ELK server is running? http://machine public ip address:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._