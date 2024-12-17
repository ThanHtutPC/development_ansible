 ## Privilege Escalation Strategies
 ```
 Ansible Playbooks can achieve privilege escalation at many levels.
 Ansible uses directives or connection variables for the privilege escalation level you intend to control.

 - Privilege Escalation in Plays
 - Privilege Escalation in Tasks
 - Grouping Privilege Escalation Tasks with Blocks
 - Privilege Escalation in Roles
 - Listing Privilege Escalation with Connection Variables
 - Choosing Privilege Escalation Approaches
 ```

## Controlling the Order of Execution
```
Ansible runs the play sections in the following order:

-pre_tasks
-Handlers that are notified in the pre_tasks section
-roles
-tasks
-Handlers that are notified in the roles and tasks sections
-post_tasks
-Handlers that are notified in the post_tasks section
```

## Running selecting tasks
```
Tagging Ansible Resources
To tag a resource, use the tags keyword on the resource, followed by a list of the tags to apply.
Running Tasks with Specific Tags (tags)
Skipping Tasks with Specific Tags (skip-tags)
Listing Tags in a Playbook (list-tags)
```

## Optimizing Execution for speed 
```
Playbook Execution 
Disabling Fact Gathering (gather_facts: false)
Reusing Gathered Facts with Fact Caching
Limiting Fact Gathering
Increasing Parallelism (forks)
Avoiding Loops with the Package Manager Modules 
- name: Ensure the packages are installed
  ansible.builtin.yum:
    name:
      - httpd
      - mod_ssl
      - httpd-tools
      - mariadb-server
      - mariadb
      - php
      - php-mysqlnd
    state: present
Profiling Playbook Execution with Callback Plug-ins
callbacks_enabled= timer, profile_tasks, cgroup_perf_recap
Timing Tasks and Roles
callbacks_enabled= timer, profile_tasks, profiles_roles
```