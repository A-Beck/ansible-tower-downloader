Ansible Tower Downloader
=========

This role downloads and extracts the Ansible Tower Installer. This is useful for initial Ansible Tower Installation, or creating workflows that re-use roles or playbooks from the installer. If you want to install Tower after downloading the installer, [request an eval license](https://www.ansible.com/license).

Requirements
------------

This role requires that the installation tarball is available over a network connection. This can be either releases.ansible.com, or an internal repository.

Role Variables
--------------

- ansible_tower_setup_version - The version of ansible tower to download. Defaults to latest
- ansible_tower_setup_url - The full uri of the Ansible Tower Setup Tarball. Set this variable to override where the ansible tower tarball is located if hosting it internally. Defaults to releases.ansible.com/ansible-tower/ansible-tower-setup-latest.tar.gz.
- ansible_tower_setup_download_username - If downloading the installer tarball requires credentials, the user required to download.
- ansible_tower_setup_download_password - If downloading the installer requires credentials, the password required to download. 
- ansible_tower_create_destinations - Create the directories where the Tower installer will be downloaded and extracted.
- ansible_tower_force_download - Always try to download the installer tarball
- ansible_tower_setup_download_location - Location on control machine to where the installer tarball will be downloaded. Defaults to the playbook directory.
- ansible_tower_setup_unarchive_location - Location where the installer tarball is extracted. Defaults to the playbook directory.
- ansible_tower_setup_link_name - Name of the link to the extracted installer. Used to make the installer directory name consistant. Defaults to `playbook_directory/ansible-tower-setup`.

Dependencies
------------

This role is not dependent on any other role.

Example Playbook
----------------

```
- name: Download the Ansible Tower Installer Tarball
  hosts: localhost
  connection: local
  gather_facts: no
  tasks:

    - name: Download the Ansible Tower Installer
      import_role:
        name: ansible-tower-downloader
      vars:
        ansible_tower_setup_version: '3.2.4'
```

Running Tests
-------------

To test this role, run the `test.yml` playbook in the test directory. The `test.yml` playbook in the test directory utilizes docker, and requires the `docker-py` package.

License
-------

BSD

