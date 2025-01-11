## Developing Ansible Content Collections
```
The Ansible community provide Ansible Content Collections for many software products and technologies.
However, customers often have automation needs that no existing collection covers.
```

## Selecting a Namespace of collections
```
Remember that Ansible organizes collections in namespaces. The namespace is the first part of a collection name.
Carefully choose a namespace for grouping your collections: 
- If you plan to publish your collections to Ansible Galaxy, then use your Ansible Galaxy username as the namespace.
- If you publish your collections to private automation hub, then ask the platform administrators to create a namespace for you. Note that you might be able to create a namespace yourself if your user account has the required permissions.
- If you are a Red Hat partner and publish your collections to automation hub, then use the namespace that Red Hat has assigned for your company.
```

## Creating the Collection Directory Structure
```
Use the ansible-galaxy collection init command to create the directory structure for your new collection.
```

## Adding Content to Collection
```
Organize the modules, plug-ins, and filters that you develop in subdirectories under the plugins/ directory.
```

## Updating Collection Metadata
```
The galaxy.yml YAML file at the root of the collection directory provides information for Ansible to build and publish the collection. The file includes comments that describe each parameter.
```

## Declaring Collection Dependencies
```
Some collections depend on other collections to work correctly.
More complex collections might provide modules, plug-ins, and filters that depend on additional Python libraries. Users must install the corresponding Python packages in the execution environment before they can use the collection.
```

## Building Collections
```
You can use the resulting .tar.gz file to install and test the collection locally, to share the collection with team members, or to publish it to a distribution platform such as Ansible Galaxy or private automation hub.
```

## Validating and Testing Collections
```
You can use the resulting .tar.gz file to install and test the collection locally, to share the collection with team members, or to publish it to a distribution platform such as Ansible Galaxy or private automation hub.
```

## Publishing Collections
```
Use the distribution platform web UI to publish your collection from the .tar.gz file.
```

## Deciding When to Create a Custom Automation Execution Environment
```
Red Hat provides several Ansible automation execution environments that suit the needs of many users. These automation execution environments include the most common Ansible Content Collections.

Preparing for a New Automation Execution Environment
-----------------------------------------------------
Create a working directory to prepare the files that you need to build the automation execution environment container image. The ansible-builder command searches this working directory for its execution-environment.yml configuration file, which it uses to determine how to build the container image.

EE_BASE_IMAGES
EE_BUILDER_IMAGES
ansible_config
galaxy
python
system
```

## Building a New Automation Execution Environment
```
The execution environment builder automatically pulls the base and the builder images if they are not already available locally.
If you use images from a container registry that requires authentication, then you must authenticate before starting the build process.
```

## Command for building a new ee 
```sh
[user@host ~]# podman login registry.redhat.io
[user@host ~]# ansible-builder build --tag ee-demo:v1.0
```

## Interacting with the Build Process
```
For more advanced configurations, you might have to customize the build process.
```

## Command build process 
```sh
[user@host ~]# ansible-builder create
[user@host ~]# podman build -f context/Containerfile -t ee-demo:v2.0 context
```

## Running a Test Playbook 
```sh
[user@host ~]# ansible-galaxy collection list 
[user@host ~]# ansible-navigator run test-playbook.yml -i inventory --eei localhost/ee-demo:v2.0 --pp never -b m stdout 
```

## Sharing an EE from private Automatic Hub 
```sh
[user@host ~]# podman tag localhost/ee-demo:v2.0 hub.lab.example.com/mynamespace/ee-demo:v2.0
[user@host ~]# podman login hub.lab.example.com 
[user@host ~]# podman push hub.lab.example.com/mynamespace/ee-demo:v2.0
```

