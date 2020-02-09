Role Name
=========

migration-analytics: Migration-analytics

[![Build Status](https://travis-ci.org/cmihai-ansible/migration-analytics.svg?branch=master)](https://travis-ci.org/cmihai-ansible/migration-analytics)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.migration-analytics](https://galaxy.ansible.com/devopstoolbox.migration-analytics)

```bash
ansible-galaxy install devopstoolbox.migration-analytics
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
migration-analytics_packages_state: present
migration-analytics_remove_packages: true
migration-analytics_enable_service: true
migration-analytics_enable_selinux: true
migration-analytics_copy_templates: true
migration-analytics_firewall_configure: true
migration-analytics_firewall_rules:
  - service: ssh
  - port: 3389
migration-analytics_users:
  - user: devops
    group: docker
migration-analytics_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install migration-analytics on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: migration-analytics is configured
      import_role:
        name: devopstoolbox.migration-analytics
      vars:
        migration-analytics_packages_state: present
        migration-analytics_remove_packages: true
        migration-analytics_enable_service: true
        migration-analytics_enable_selinux: true
        migration-analytics_copy_templates: true
        migration-analytics_firewall_configure: true
        migration-analytics_firewall_rules:
          - service: ssh
          - port: 3389
        migration-analytics_users:
          - user: devops
            group: docker
        migration-analytics_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: migration-analytics
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
