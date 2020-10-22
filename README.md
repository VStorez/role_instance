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

### For EC2

| Variable Name | Description | Mandatory | Additional information |
|--|--|--|--|
| ec2_keypair | Name of the keypair which will be injected into the VM | yes | Keypair must exist in AWS console |
| instance_type | linux / windows | yes | |
| ec2_region | Which AWS region to provision the resources to | yes |
| ec2_key_file | Needed to obtain Windows Administrator password | no | "<Path/To/KeyFile.pem>" |
| ec2_ami_id | Which AMI to use as a template | no | e.g. ami-04cf43aca3e6f3de3 |
| ec2_image_name | Regexp for AMI's to search from AWS | no | e.g. "RHEL-7.9_HVM_GA*x86_64*" |

## TODO

Support more providers. Right now GCP is the only tested provider.
