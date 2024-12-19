## Delegating Tasks 
```
Ansible is running a play to ensure the correct configuration of a system, it might need to perform one or more tasks on another host on behalf of the managed host. 
In a play, you can delegate a task to run on another host instead of the current managed host. 
A task delegates the action to a host by using the delegate_to directive. 
```

## Delegating facts
```
Ansible use the host variables and facts for the managed host (the current inventory_hostname) for which the task is running. 
```

## Configuring Parallelism
```
Ansible processes a playbook, it runs each play in order. After determining the list of hosts for the play, Ansible runs through each task in order. 
Ansible could connect to all hosts in the play simultaneously for each task. (default forks = 5)
```

## Running Batches of hosts Through the entire play
```
Ansible runs a play, it ensures that all managed hosts complete each task before it starts the next task. After all managed hosts have completed all tasks, then any notified handlers are run. (serial)
```

Setting Batch Size a Percentage
Setting Batch Size to change during the play 
