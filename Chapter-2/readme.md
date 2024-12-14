## Defining Ansible Content Collections
```
Ansible Content Collection are a distribution format for ansible content. A collection provides related modules, roles, playbooks and plug-ins that you can download to your control node and then use in playbook. 
```

## Organizing Ansible Content Collection in Namespace 
```
To make it easier to specify collections and their contents by name, collections names are organized into namespaces. 
```

## Using Ansible Content Collections 
```
The automation execution environment that Red Hat provides already include some collections. You can install additional collections on your local system or create a custom automation execution environment that incorporates these collections.
```

## Accessing Ansible Content Collection Documentation 
```
The ansible-navigator collections command to list the collections available in automation execution environments
```

## Command Ansible Content Collection 
```sh 
[user@host ~]$ podman login hub.lab.example.com 

[user@host ~]$ ansible-navigator doc redhat.insights.insights_register --mode stdout
```

## Using Ansible Content Collections in playbooks 
```
To use a module or a role from a collection, refer to it with its fully qualified collection name (FQCN). 
```

## Example for Ansible Content Collection.
```yaml
---
- name: Register new systems
  hosts: db.example.com

  tasks:
    - name: Ensure the new system is registered with Red Hat Insights
      redhat.insights.insights_register:
        state: present
        force_reregister: true
```

## Using the Built-in Ansible Content Collection 
```
Ansible always includes a special collection named ansible.builtin. This collection includes set of common modules, such as copy, template, file, yum, command and service. 
```

## Command verify ansible-doc 
```sh
[user@host ~]$ ansible-doc -l | grep firewalld

[user@host ~]$ ansible-doc ansible.posix.firewalld
```

## Source for Ansible Content Collection
```
Ansible Hub 
Ansible Galaxy
```

## Installing Ansible Content Collection
```sh 
[user@host ~]$ ansible-galaxy collection install community.crypto
[user@host ~]$ ansible-galaxy collection install ./o1labs-crypto-0.1.5.tar.gz -p collections/
```

## Installing Collections with a Requirements File
```
The collections/requirements.yml file is a list of the collections needed to run playbook in your Ansible Project, just like you can create a roles/requirements.yml file list the roles that you need to install.
```

## Example for collections/requirements.yml
```yaml 
---
collections:
  - name: community.crypto

  - name: ansible.posix
    version: 1.2.0

  - name: /tmp/community-dns-1.2.0.tar.gz

  - name: http://www.example.com/redhat-insights-1.0.5.tar.gz

  - name: git@github.com:ansible-collections/community.mysql.git
```

## Ansible content collection run for listing 
```
[user@host ~]$ ansible-galaxy collection install -r collections/requirements.yml -p collections/ 
```

## Command for ansible content collections list 
```sh 
[user@host ~]$ ansible-navigator collection
[user@host ~]$ ansible-galaxy collection list 
```

## Installing Collections from Automation Hub
```ini
[galaxy]
server_list = automation_hub, galaxy (1)

[galaxy_server.automation_hub]
url=https://console.redhat.com/api/automation-hub/ (2)
auth_url=https://sso.redhat.com/auth/realms/redhat-external/protocol/openid-connect/token (3)
token=eyJh...Jf0o (4)

[galaxy_server.galaxy]
url=https://galaxy.ansible.com/
```

## Automatic Execution Environment
```
An Automatic Execution Environment is a container image that includes Ansible Content Collections, their software dependencies, and a minimal Ansible engine that can run your playbook. 

Selecting a Supported Automation Execution Environment
-------------------------------------------------------------
- registry.redhat.io/ansible-automation-platform-22/ee-minimal-rhel8:latest
- registry.redhat.io/ansible-automation-platform-22/ee-supported-rhel8:latest
- registry.redhat.io/ansible-automation-platform-22/ee-29-rhel8:latest

pull-policy
- always 
- missing 
- never 
- tag
```
