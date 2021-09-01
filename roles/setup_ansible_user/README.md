Role Name
=========

A simple role to deploy a user for ansible on managed node.

Requirements
------------

Access to remove machine with sudo or root access.

Role Variables
--------------

```
# username to be created on remote machine for ansible
remote_user_name: 'devops'
remote_user_password: 'mypassword'

# public key string for same user.
# if not provided, role will skip adding public key to target machine.
remote_user_public_key: <public key string>
```

Dependencies
------------

None

Example Playbook
----------------

**Sample playbook**
```
- hosts: servers
  become: true
  vars:
    remote_user_name: 'devops'
    remote_user_password: 'mypassword'
    remote_user_public_key: '<public key string>'
  roles:
    - { role: ginigangadharan.setup_ansible_user }

```

Use it with privileged user for first time as below.

```
ansible-playbook setup-ansible.yaml -b -K -k -u root
```

License
-------

BSD

Author Information
------------------

This role was created by [Gini](https://www.iamgini.com).
