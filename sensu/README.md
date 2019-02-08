These playbooks are setup in roles which dynamically pick up two things dynamically based on ansible_hostname:
* Environment as (cl)?(dev|test|stage|prod)
* Client (code)
* Additionally, the playbooks are dependant on the POD definition being up-to-date in the host manifest.

##### Fresh Install of Sensu
`ansible-playbook sensu_install.yml -k -K --user=MYUSER -e "target=abc-dev"`

##### Update of Sensu
`ansible-playbook sensu_update.yml -k -K --user=MYUSER -e "target=abc-dev"`

##### Decom/Discontiue Sensu
`ansible-playbook sensu_decom.yml -k -K --user=MYUSER -e "target=abc-dev"`

Sensu Client Registration
=========

Registers a Host to sensu server. Roles are assigned based on hostname.

Requirements
------------

N/A

Role Variables
--------------

  - `relative_hostname`: Used to prevent role clashes, so that `pro[db]ackend` nodes are not also defined as `db` hosts.

Group Variables
------------

  - `env_level`: Used to define which environment, such as dev/test/stage/prod.  Modify this to match your environment.
  - `client_code`: Used to define client, so ensure alerts reach the right on-call staff.  Modify this to match your enironment.

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
         - install
         - { role: ROLE1, when: relative_hostname | search ("ROLE1") }
         - { role: ROLE2, when: relative_hostname | search ("ROLE2") }
         - { role: ROLE3, when: relative_hostname | search ("ROLE3") }
         - { role: ROLE4, when: relative_hostname | search ("ROLE4") }
         - { role: ROLE5, when: relative_hostname | search ("ROLE5") }
         - { role: ROLE6, when: relative_hostname | search ("ROLE6") }
         - { role: ROLE7, when: relative_hostname | search ("ROLE7") }

License
-------

Commercial

Author Information
------------------

[Rick Mulder](https://github.com/rickymulder/ansible)
