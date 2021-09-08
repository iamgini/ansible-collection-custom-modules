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

Sample playbooks are available in [playbooks](playbooks) directory.

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
# Sharing Collection to Ansible Galaxy

Always contribute back to the community !

You can use either the GUI method (browsing the Zip file and upload to Ansible Galaxy) or the CLI method with API token. 

## Publishing Ansible Collection using Ansible Playbook

I have an Ansible playbook which will build and publish the Ansible Collection with proper version tag. 

```shell
% ansible-playbook utilities/update-collection.yaml -e "tag=1.0.10"
```

## Publishing Ansible Collection Manually

**Building the collection archive**

build command will create the collection archive with version information which you can publish to Ansible Galaxy (CLI or GUI).

```shell
$ ansible-galaxy collection build
# --force to overwrite if any existing archive with same version 

% ls -la *.tar.gz
-rw-r--r--  1 gini  staff  7023  8 Sep 11:12 ginigangadharan-custom_modules-1.0.10.tar.gz
```

**Publish the Collection to Ansible Galaxy**

Make sure you have created the Ansible Galaxy API Token and exported as environment variable `ANSIBLE_GALAXY_TOKEN` before you call the publish command.

```shell
$ ansible-galaxy collection publish \
  ./ginigangadharan-custom_modules-{{ tag }}.tar.gz \
  --api-key $ANSIBLE_GALAXY_TOKEN \
  --ignore-certs
```

## Appendix

### Adding Roles as Submodules (Not used)

```shell
$ git submodule add https://github.com/ginigangadharan/setup-ansible-user

$ cat .gitmodules 
[submodule "roles/setup-ansible-user"]
        path = roles/setup-ansible-user
        url = https://github.com/ginigangadharan/setup-ansible-user
```