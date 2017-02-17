Chrony
=======
[![Build Status](https://travis-ci.org/ISU-Ansible/ansible-chrony.svg?branch=master)](https://travis-ci.org/ISU-Ansible/ansible-chrony)

Note, this role is meant to install and configure the chronyd service on an Enterprise Linux system. This role should function on EL 6, EL 7, and Fedora systems.

Requirements
------------
No requirements

Role Variables
--------------

* **chronyd_configuration_file**: /etc/chrony.conf
* **chronyd_servers**: This option expects a list of the following attributes.
  * **address**: address of server
  * **type**: server or pool
  * **options**: other options for the server
* **chronyd_makestep_offset**: 10
* **chronyd_makestep_updates**: 3
* **chronyd_driftfile**: /var/lib/chrony/drift
* **chronyd_stratumweight**: "0"
* **chronyd_rtcsync**: true
* **chronyd_allow**: []. Note that this option will accept a list.
* **chronyd_bindcmdaddress**: Note that this option will accept a list of values
  - "127.0.0.1"
  - "::1"
* **chronyd_commandkey**: "1"
* **chronyd_generatecommandkey**: true
* **chronyd_noclientlog**: false
* **chronyd_keyfile**: /etc/chrony.keys
* **chronyd_logchange**: "0.5"
* **chronyd_logdir**: "/var/log/chrony"

Defaults
--------
```
chronyd_configuration_file: /etc/chrony.conf

chronyd_servers:
  - address: 0.pool.ntp.org
    type: pool
    options: offline
  - address: 1.pool.ntp.org
    type: pool
    options: offline
  - address: 2.pool.ntp.org
    type: pool
    options: offline
  - address: 3.pool.ntp.org
    type: pool
    options: offline

chronyd_makestep_offset: 10
chronyd_makestep_updates: 3

chronyd_driftfile: /var/lib/chrony/drift
chronyd_stratumweight: "0"
chronyd_rtcsync: true

chronyd_allow: []
chronyd_bindcmdaddress:
  - "127.0.0.1"
  - "::1"

chronyd_commandkey: "1"
chronyd_generatecommandkey: true

chronyd_noclientlog: false

chronyd_keyfile: /etc/chrony.keys
chronyd_logchange: "0.5"
chronyd_logdir: "/var/log/chrony"
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
