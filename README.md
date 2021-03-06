This Ansible role installs and configures Jira on a Debian servers.
Following actions will be taken to install Jira:
- Download Jira binary and make it executable.
- Install or Upgrade Jira, if a newer Version is downloaded.
- Move Backups & Upgrade-Information into the backup folder.
- Configure ReverseProxy Connectors for Jira, if enabled. 

## Requirements
No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:
    - hosts: jira
      become: yes
      roles:
        - jira

## Role Variables
Available variables are listed below. Most of them are saved as role defaults (see `defaults/main.yml`):  
### Installation
    jira_installer_name: atlassian-jira-software-7.13.0-x64.bin  
    jiraAsService: true 
    jiraWithReverseProxy: false  
    server_baseurl: jira.example.com  
### Paths
    atlassian_root: /opt/atlassian
    jiraHomePath: /var/atlassian/apllication-data/jira
### Ports
    differentPorts: false
    rmiPort: 8005
    httpPort: 8080

## Example Playbook
    - hosts: jira
      become: yes
      roles:
        - jira