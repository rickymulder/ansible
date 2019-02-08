Spacewalk Registration
=========

Registers a Host to it's appropriate Spacewalk server based on the hostname.

Requirements
------------

N/A

Role Variables
--------------

- `client_version`: Set this to the client version repo. See [the spacewalk archive](https://copr-be.cloud.fedoraproject.org/archive/spacewalk/) for available options. Please note, this is setup to use 2.6.  Newer clients may require you upgrade the spacewalk host as well.
- `env`: Defines the datacenter the host resides in. Used to declare which spacewalk host to register to. Please modify this to fit your use-case.


Group Variables
------------

N/A

Dependencies
------------

N/A

Example Playbook
----------------

In your Ansible playbook:

    - hosts: "{{ target }}"
      become: true
      become_method: sudo
      gather_facts: true
      roles:
         - register

License
-------

Commercial

Author Information
------------------

[Rick Mulder](https://github.com/rickymulder/ansible)
