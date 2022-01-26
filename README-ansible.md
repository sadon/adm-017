### TF поднимаем машину - и получаем ssh ключ

### Пишем inventory
`ansible all -m ping -i ./inventory-hosts.ini`

### Справка

По образу и подобию
https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-wordpress-with-lamp-on-ubuntu-18-04-ru

### Настраиваем переменные
Меняем http_host/ vars/default.yaml

~/Projects/_other/adm-017/ansible-playbooks/wordpress-lamp_ubuntu1804:

### Применяем playbook
ansible-playbook playbook.yml -l wphost -i ../../inventory-hosts.ini