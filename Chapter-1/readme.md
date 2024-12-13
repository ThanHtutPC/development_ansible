## Ansible-core
```
Red Hat Ansible Automation Platform 2.2 provides Ansible Core 2.13 in the ansible-core RPM package.
```

## Ansible content collection
```
Ansible-core provide "ansible.builtin" ansible content Collection. 
```

## Ansible Content Navigator
```
Ansible Automation Platform 2 provides a new top-level develop and test Ansible Playbooks, Automation content navigator(ansible-navigator). The tools replaces and extends the functionally of servel earlier command-line utilites. (ansible-playbook, ansible-inventory, ansible-config)

Automatic content navigator with seperate with control node, on which you run Ansible, from the automatic execution environment that runs it, by running your playbooks in a container. 
```

## Automatic Execution Environment 
```
Automatic Execution environment is a container images that contains Ansible Core, Ansible Content Collection, Python libraries, executables or other dependencies needed to run your playbook.

Automatic execution environment is a ansible controller. 
```

## Ansible Controller 
```
Ansible Controller is formerly called RedHat Ansible Tower. It provides a web UI and a REST API that can be used to configure, run and evaluate your automatic jobs. If automatic code required a difference set of python dependencies in the execution environment on Ansible Tower than the system provide by default, you had to manually set up a seperate Python virtual environements ("venv") for your automatic code to use. 

Control plane 
Automatic job 
- Self-service
- Approval
- Role-based access control 

Execution plane 
- Environments 
```

## Automatic Hub
```
Automatic hub provides you with a way to manage and distribute automatic content. A public service at "console.redhat.com" provide access to Red Hat Ansible Certified Content Collections that you can download and use the "ansible-galaxy" (for ansible-navigator) and automatic controller.
```

## Install the Ansible Content Navigator
```
[user@host ~]$ subscription-manager register 


[user@host ~]$ subscription-maanager repos --enable ansible-automation-platform

[user@host ~]$ sudo yum install ansible-navigator 
```

## Ansible-navigator Command 
```sh
Test-Base in format 
[user@host ~]$ ansible-navigator run playbook.yml -i inventory

Playbook in the same format 
[user@host ~]$ ansible-navigator run playbook.yml -i inventory --mode stdout
```

## Change the execution environment images for run the ansible-navigator 
```
[user@host ~]$ podman login registry.redhat.io 

[user@host ~]$ podman login hub.lab.example.com

[user@host ~]$ ansible-navigator run playbook.yml -i inventory --mode stdout --eei registry.redhat.io/ansible-automation-platform-24/ee-supported-rhel8 
```

## Reviewing Previous Playbook Runs
```sh
[user@host ~]$ ansible-navigator replay 
```

## Read Documentation
```sh
[user@host ~]$ ansible-navigator doc ansible.posix.firewalld
```

## Git init configuration
```
Git is a distributed version control system (DVCS) 
You can review and restore earlier versions of files.
You can compare two versions of the same file to identify changes.
You can record a log of who made what changes, and when those changes were made.
Multiple users can collaboratively modify files, resolve conflicting changes, and merge the changes.
```

## Command Git Configuration
```sh
[user@host ~]$ git config --global user.name "peter"
[user@host ~]$ git cofnig --global user.email "peter@gmail.com" 
```

## Command for git config 
```sh
[user@host ~]$ git config --global push.default simple 
[user@host ~]$ git config --global credential.https://git.lab.example.com.username student 
```

## Command for git branchs
```sh 
[user@host ~]$ git checkout -b feature/3
[user@host ~]$ git branch feature/3

Pushing Branches to Remote repositories 
[user@host ~]$ git push --set-upstream origin feature/3
```

## Configure Git ignore file 
```
Configre git to ignore file and directories that should not be trackes or committed. To instruct Git to ignore specific files and paths in your project, add a .gitignore file.
```

## git scenario inital 
```sh 
[user@host ~]$ git init  
[user@host ~]$ git clone git@git.lab.example.com:project-git
[user@host ~]$ git add .
[user@host ~]$ git commit -m -a "update commit"
[user@host ~]$ git push --set-upstream origin upstream
```