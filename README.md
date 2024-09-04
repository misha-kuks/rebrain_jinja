### Плейбук показывает как работает шаблонизатор jinja

```
ansible-playbook -i inventory.yaml site.yaml 

PLAY [Nginx config] *****************************************************************************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************************************************
ok: [web01]

TASK [Install Nginx] ****************************************************************************************************************************************************************************************
ok: [web01]

TASK [Enable nginx.service] *********************************************************************************************************************************************************************************
ok: [web01]

TASK [Update nginx default config] **************************************************************************************************************************************************************************
changed: [web01]

TASK [Remove html default and default site] *****************************************************************************************************************************************************************
changed: [web01] => (item={'dest': '/etc/nginx/sites-enabled/default'})
changed: [web01] => (item={'dest': '/var/www/html/index.nginx-debian.html'})

TASK [Copy site conf template] ******************************************************************************************************************************************************************************
changed: [web01]

TASK [Create symlink] ***************************************************************************************************************************************************************************************
changed: [web01]

TASK [Create html templates loop] ***************************************************************************************************************************************************************************
changed: [web01] => (item={'name': 'orange', 'price': 160, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Salustiana'})
changed: [web01] => (item={'name': 'apple', 'price': 220, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Golden'})
changed: [web01] => (item={'name': 'baNana', 'price': 120, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Lady Finger'})
changed: [web01] => (item={'name': 'AvocaDo', 'price': 220, 'currency': 'rub', 'serving': 2, 'measure': 'pcs', 'description': 'Gwen'})
changed: [web01] => (item={'name': 'cucumber', 'price': 70, 'currency': 'rub', 'serving': 1, 'measure': 'pcs', 'description': 'Bella'})

TASK [Create index.html] ************************************************************************************************************************************************************************************
changed: [web01] => (item={'name': 'orange', 'price': 160, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Salustiana'})
ok: [web01] => (item={'name': 'apple', 'price': 220, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Golden'})
ok: [web01] => (item={'name': 'baNana', 'price': 120, 'currency': 'rub', 'serving': 1, 'measure': 'kg', 'description': 'Lady Finger'})
ok: [web01] => (item={'name': 'AvocaDo', 'price': 220, 'currency': 'rub', 'serving': 2, 'measure': 'pcs', 'description': 'Gwen'})
ok: [web01] => (item={'name': 'cucumber', 'price': 70, 'currency': 'rub', 'serving': 1, 'measure': 'pcs', 'description': 'Bella'})

RUNNING HANDLER [reload nginx] ******************************************************************************************************************************************************************************
changed: [web01]

PLAY RECAP **************************************************************************************************************************************************************************************************
web01                      : ok=10   changed=7    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```