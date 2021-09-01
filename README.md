# Ansible Collection

Collection Name: ginigangadharan.custom_modules

Install this collection locally:

```shell
ansible-galaxy collection install ginigangadharan.custom_modules
```

## Testing Modules


```shell
$ ansible-playbook playbooks/3-hello-python yaml
```
## Sample Playbooks

Sample playbooks are available in [playbooks](playbooks) directory

Sample Playbook
```yaml
---
- name: Testing Custom Module
  hosts: nodes
  gather_facts: false
  tasks:
    - name: Calling customhello2 module
      hello_message:
        message: "Hello"
        name: "John"
      register: custom_value

    - debug:
        msg: "{{ custom_value }}"
```