# ansible_key
управление ssh ключами пользователей на удаленных хостах

ansible_key/   
**-inventory**   
--ip.ini - файл содержащий ип адреса серверов к которым будет подключаться ансибл   
**-roles**   
--tasks   
---main.yml - файл содержащий основную роль которая подключается к серверу к указаному пользователю и изменяет его authorized_keys   
--templates
---authorized_keys.j2 - шаблон по которому формируется ..ssh/authorized_keys у пользователя на удаленном сервере   
--vars
---main.yml - в данном файле указывается имя пользователя и соответсвующие ему ключи

### Формат vars/main.yml
```bash
users:
  test2:
    - "ssh-rsa key user@srv"
    - "ssh-rsa key user@srv"
    - "ssh-rsa key user@srv"
```


### Пример запуска:

```
ansible-playbook -i inventory/ip.ini keys.yml -u root
``` 
