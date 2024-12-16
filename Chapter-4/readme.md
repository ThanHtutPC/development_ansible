## Ansible Content Navigator 
```
Ansible Configuration in Interactive Mode 
    Example- ansible-navigator run, ansible-navigator config
```

## Searching in Configuration
```
Searching for Specific Configuration Parameters Type ":filter(or :f)" 
    Example- :f forks, :f ansible.cfg
Accessing Parameter Details
    - current value = actual parameter 
    - default vaule = parameter's default value 
    - name: ANSIBLE_FORKS = environment variable that you can use parameter value 
    - forks = parameter's value in an ansible.cfg 
```

## Command for Searching Configuration
```sh 
# do edit io the ansible.cfg
[user@host ~]# ansible-navigator config --eei hub.lab.example.com/ee-supported-rhel8:latest --pp missing 

:filter Inventory
```

## Inspecting the Local Configuration 
```
"ansible-navigator" command does not use in the "/etc/ansible.ansible.cfg" or "~/.ansible.cfg". To process those local file, use "--execution-environment false(or --ee false)".

"--mode stdout" is a standared output. This command is change interactive to standard"
```

## Command for Standard output 
```sh
[user@host ~]# ansible-navigator config --mode stdout dump
```

## Content Ansible Navigator 
```
The settings file can be json or yaml format. 
For settings in Json format. the extension must be .json. 
For settings in yaml format. the extension mush be .yml or yaml. 
```

## Locating the setting file
```
Ansible Environment variables is set. (ANSIBLE_NAVIGATOR_CONFIG)
The "ansible-navigator.yml" file in your current Ansible Project directory. 
A "~/.ansible-navigator.yml" file (in your home directory). Notice that is "dot" at the start of its file name. 
```

## Generating a setting file
```
You can use the ansible-navigator settings command to generate settings file. 
"--sample" option, then the command outputs a sample ansible-navigator configuration.
"--effective" option, than the command current effective configuration for ansible-navigator.
```

## Command generating a setting file
```sh
[user@host ~]$ ansible-navigator settings --effective --pp missing --eei ee-supported-rhel8 > /tmp/ansible-navigator.yml
[user@host ~]$ ansible-navigator run site.yml --eei ee-29-rhel8 --pp always
```

## Important 
```
Disabling playbook artifact creation enables you to run the playbook interactively. Running interactively is useful when you want to use options such as --ask-vault-pass on the command line. 
However, disabling artifact creation removes the ability to run ansible-navigator reply.
```

## password generate 
```sh 
[user@host ~] mkpasswd -m sha-512 "test123@"
```