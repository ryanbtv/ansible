```
cd $ANSIBLE_HOME/deploy_zabbix_server
ansible-galaxy install -r requirements.yml
ansible-playbook plays/deploy_zabbix.yml -i hosts --ask-vault-pass
```