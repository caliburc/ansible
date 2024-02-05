# Deploy Multiple VMware VM with Ansible

## Description

Playbook and role to deploy multiple vSphere virtual machines from a template using Ansible. For more information, you can refer to the [related blog post](https://cloudmaniac.net/deploy-multiple-vm-with-ansible-on-vsphere/).

## Requirements
* Python (≥ 2.6)
* Ansible
* PyVmomi

## Configuration
The required files are:
```
├── ansible.cfg
├── deploy-vms.yml
├── roles
│   └── deploy-vsphere-template
│       └── tasks
│           └── main.yml
├── vars
│   └── answerfile.yml
│   └── secrets.yml
└── vms-to-deploy
```

1. Edit the ```vms-to-deploy``` file to define the number of virtual machines you want to deploy, as well as their names, datastore, IP and notes.
2. Edit the ```answerfile.yml``` file to set the correct parameter for
    * the infrastructure (where to deploy)
    * the common options for the virtual machines
4. Edit the ```secrets.yml``` file to set username\password for vsphere
5. (optional) Edit the role.

> **Note:** Uncomment the `#resource_pool: '{{ deploy_vsphere_resourcepool }}'` line in the `roles/deploy-vsphere-template/tasks/main.yml` file to deploy the virtual machines in a specific resource pool; don't forget to reflect your resource pool name in the `answerfile.yml`.

## Execution

```
ansible-playbook deploy-vms.yml
```

## Optionally you can build a seperate inventory file
```
ansible-playbook -i my-new-inventory deploy-vms.yml
````

