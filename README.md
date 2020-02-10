# Ansible Playbook: Using ACI with MSO and VMM domains

## Ansible with ACI and MSO with VMM domains

This Ansible playbook consists of multiple plays of ACI, MSO, and vCenter.

The following tasks will be completed:
* Create a Tenant 
* Create a VRF 
* Create a Bridge Domain 
* Create a Subnet 
* Create an Application Profile
* Create EPGs (3 EPGs)
* Create a Filter 
* Create a Filter Entry 
* Create a Contract 
* Create a Contract Subject and form a relationship to the filter 
* Relate each EPG to a VMM Domain
* Assign portgroups to the VMM domain

## Requirements

This playbook requires the standard set of ACI and MSO modules from Ansible v2.7.

## Installation

Installing Ansible to run your playbooks:

1. Using the link provided below - install and run from source
```
https://docs.ansible.com/ansible/devel/installation_guide/intro_installation.html#running-from-source
```
_It's recommended to do a git clone and run from the developers branch_

## Using the mso.yml playbook

Configure your APIC host and credentials

Look inside the hosts inventory and provide the needed information. Only the first APIC, MSO, and vCenter is being used by the playbook.

#### Running the mso.yml playbook

##### **Note: Ensure to delete all configurations before running the mso.yml playbook again to avoid a 500 Internal Server Error in the _mso_schema_template_contract_filter_ module (has been reported and currently debugging)**

Run the following command using Ansible v2.7:

```
ansible-playbook -i ./hosts mso.yml
```

The first time it will deploy that configuration on your ACI infrastructure.

```
ansible-playbook -i ./hosts delete-all.yml
```

You can make modifications and run it again _after running delete-all.yml_ as often as you like to modify the existing configuration.

## Notes

- Over time when more ACI and MSO modules are released with Ansible, we will swap the aci_rest calls with the high-level module calls.
- Feel free to add additional functionality or report bugs and share it with us on Github https://github.com/ansible/ansible!

## License

Apache License 2.0
