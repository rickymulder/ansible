# All things sensu

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
