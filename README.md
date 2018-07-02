To run playbooks use following commands

export GUID=<your GUID>

To run all four roles

ansible-playbook -i myinventory.file playbook.yml --tags common,haproxy,postgresql,app  -e "GUID=${GUID}"

To run single role

ansible-playbook -i myinventory.file playbook.yml --tags haproxy  -e "GUID=${GUID}"


To clean up 

ansible-playbook -i myinventory.file playbook.yml --tags cleaner  -e "GUID=${GUID}"


To verify application and loadbalancer

curl http://frontend1.${GUID}.example.opentlc.com/
Do this curl twice and you will observe the message that hostname changes on next curl (round robin)

You can check other apps as well

curl http://frontend1.${GUID}.example.opentlc.com/inder/index.html
curl http://frontend1.${GUID}.example.opentlc.com/ansible/index.html
