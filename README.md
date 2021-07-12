# Ansible Role: Instance

This role will help to create and remove instances on several different providers. It can also be used to demonstrate multi cloud use cases.

## How to install this role

It's recommended to use the [Ansible SSA Collection](https://gitlab.com/redhat-cop/ansible-ssa/ansible-ssa-collection) instead of using this role directly. Add the following line to your `collections/requirements.yml`:

```yaml
---
collections:
  # replace version below
  - https://gitlab.com/redhat-cop/ansible-ssa/ansible-ssa-collection/-/raw/master/ansible_ssa-common-<version>.tar.gz

```

If you really don't want to use the Collection, you can specify the role in your `roles/requirements.yml`:

```yaml
- src: https://gitlab.com/redhat-cop/ansible-ssa/role-instance.git
  name: instance
```

## How to use this role

Call the role from your playbook like this:

```yaml
- name: deploy instance
  var:
    type: gcp
    instance_name: demo
    instance_flavor: n1-standard-1
  include_role:
    name: instance
```

To remove or delete a VM or instance, use the same role, but with the "remove" variables set to true.

```yaml
- name: remove instance
  var:
    type: gcp
    instance_name: demo
    remove: true
  include_role:
    name: instance
```

## Variables

Check the [defaults/main.yml](defaults/main.yml) for details on variables used by this role.
