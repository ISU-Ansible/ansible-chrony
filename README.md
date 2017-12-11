Chrony
=======
[![Build Status](https://travis-ci.org/ISU-Ansible/ansible-chrony.svg?branch=master)](https://travis-ci.org/ISU-Ansible/ansible-chrony)

Note, this role is meant to install and configure the chronyd service on an Enterprise Linux system. This role should function on EL 6, EL 7, and Fedora systems.

By default, this role will use the configuration in the **chrony_defaults** variable, located in vars/{{ansible_distriution}}.yml. If you have a similar key in the **chrony** variable, then it will override the key in **chrony_defaults**. Additionally, any variable named **chrony_<key>** will override a **chrony[key]** and **chrony_defaults[key]** variable. 

Requirements
------------
No requirements

Role Variables
--------------
* **chrony**: key/value store for the chrony configuation

Other variables should not be modified unless you are sure what you are doing.

Defaults
--------
```
chrony_configuration_file: /etc/chrony.conf
chrony_config_owner: chrony
chrony_config_group: chrony
chrony_config_mode: 0644
chrony_service: chronyd

chrony:
  servers:
    - "0.pool.ntp.org pool offline"
    - "1.pool.ntp.org pool offline"
    - "2.pool.ntp.org pool offline"
    - "3.pool.ntp.org pool offline"
  makestep_offset: 10
  makestep_updates: 3
  driftfile: /var/lib/chrony/drift
  stratumweight: "0"
  rtcsync: true
  keyfile: /etc/chrony.keys
  logchange: "0.5"
  logdir: "/var/log/chrony"
```

Dependencies
------------
No dependencies.

Example Playbook
----------------
    - hosts: systems
      roles:
         - { role: ISU-Ansible.chrony }

License
-------
GPL2

Author Information
------------------
* [Barry Britt (bbritt@iastate.edu)](bbritt@iastate.edu)
* [John Dickerson (jedicker@iastate.edu)](jedicker@iastate.edu)
