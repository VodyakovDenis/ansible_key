# ansible_key
управление ssh ключами пользователей на удаленных хостах

### inventory   
- ip.ini - файл содержащий ип адреса серверов к которым будет подключаться ансибл   

### roles/tasks   
- main.yml - файл содержащий основную роль которая подключается к серверу к указаному пользователю и изменяет его authorized_keys   

### roles/templates
- authorized_keys.j2 - шаблон по которому формируется ..ssh/authorized_keys у пользователя на удаленном сервере   

### roles/vars
- main.yml - в данном файле указывается имя пользователя и соответсвующие ему ключи

### keys.yml 
- плейбук

### ping.yml
- плейбук проверки доступности хостов

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
