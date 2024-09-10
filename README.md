Node Role
=========

This role allows the deployment of the Zeek Suricata node with Fluentd Log forwarder:

1. Zeek
2. Suricata
3. Fluentd

Requirements
------------

Ubunto 22.04

Role Variables
--------------

N/A.

Dependencies
------------

If using Ubuntu 24.04 or newer comment task that adds suricata 

Molecule Testing
----------------

Execute from role base directory for each Molecule operation:

    MOLECULE_DISTRO=ubuntu:focal molecule create
    MOLECULE_DISTRO=ubuntu:focal molecule converge
    MOLECULE_DISTRO=ubuntu:focal molecule test
    MOLECULE_DISTRO=ubuntu:focal molecule destroy


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
#Example playbook
- name: Install Suricata Zeek for target1
  hosts: target1
  become: yes
    
  tasks:
    - name: "Print a message before role execution"
      ansible.builtin.debug:
        msg: "Tasks to run before role execution"
    
    - name: "Setup Zeek and Suricata node on  target1"
      import_role:
        name: "ids.node_role"
      vars:
        interface_management: enp0s3
        interface_listener: enp0s7
        aggregator_primary_ip_zeek: 10.0.56.131
        aggregator_primary_port_zeek: 24224
        aggregator_secondary_ip_zeek: 10.0.56.132
        aggregator_secondary_port_ip_zeek: 24224
        aggregator_primary_ip_suricata: 10.0.56.131
        aggregator_primary_port_suricata: 24224
        aggregator_secondary_ip_suricata: 10.0.56.132
        aggregator_secondary_port_ip_suricata: 24224
    
    - name: "Print a message after role execution"
      ansible.builtin.debug:
        msg: "Tasks to run after role execution"
```
 


License
-------

BSD

Author Information
------------------

JCPS
