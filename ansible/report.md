1. Cmds :
Tester la connexion
ansible all -i inventories/setup.yml -m ping

Découvrir les facts
ansible all -i inventories/setup.yml -m setup -a "filter=ansible_*"

Désinstaller un pakcage
ansible all -i inventories/setup.yml -m apt -a "name=apache2 state=absent" --become

2. Le playbook utilise un rôle nommé `docker` pour installer et configurer Docker Engine
- `inventory.yml` : fichier d'inventaire des hôtes à configurer.
- `roles/docker/tasks/main.yml` : contient toutes les étapes pour installer Docker, ses dépendances, le SDK Python, et vérifier que le service est démarré.
- `playbook.yml` : playbook principal qui appelle le rôle `docker`.
```bash
ansible-playbook playbook.yml -i inventory.yml
```