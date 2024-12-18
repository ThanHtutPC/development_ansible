## Providing Default Variable Values
```
- name: Manage user
  ansible.builtin.user:
    name: "{{ item['name'] }}"
    groups: "{{ item['groups'] | default(omit) }}" 
    system: "{{ item['system'] | default(false) }}" 
    shell: "{{ item['shell'] | default('/bin/bash') }}" 
    state: "{{ item['state'] | default('present') }}" 
    remove: "{{ item['remove'] | default(false) }}" 
  loop: "{{ user_list }}"
```
