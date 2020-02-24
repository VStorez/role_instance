# Ansible Role: Instance

This role will help to create and remove instances on several different providers. It can also be used to demonstrate multi cloud use cases.

## How to use this role

Call the role from your playbook like this:

	- name: deploy instance
	  var:
	    type: gcp
	    instance_name: demo
	    instance_flavor: n1-standard-1
	  include_role:
	    name: instance

To remove or delete a VM or instance, use the same role, but with the "remove" variables set to true.

	- name: remove instance
	  var:
	    type: gcp
	    instance_name: demo
	    remove: true
	  include_role:
	    name: instance

## Variables

| Variable Name | Description | Mandatory |
|--|--|--|
| type | Provider Type, gcp, ec2, rhv or vmw | yes |
| instance_name | Name of the VM or Instance | yes |
| instance_flavor | e.g. n1-standard-1 for a small VM on GCP | yes |

## TODO

Support more providers. Right now GCP is the only tested provider.
