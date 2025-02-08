# ansible
Простейшая конфигурация для работы с 3 тестовыми ВМ.
##Перед началом:
Посмотреть hosts файл
Посмотреть файл конфигурации (ansible.cfg)
## Модули
проверить доступ до хостов
```bash
ansible testing -m ping
```
постмотреть аптайм и LA
```bash
ansible all -m shell -a "uptime"
```
посмотреть оперативную память
```bash
ansible all -m shell -a "free -h"
```
посмотреть место на диске
```bash
ansible all -m shell -a "df -Th"
```
передать файл
```bash
ansible all -m copy -a "src=./files/testing.file dest=/tmp" -b
Проверить наличие файла
```bash
ansible all -m shell -a "ls /tmp | grep test" -b
```
удалить файл
```bash
ansible all -m file -a "path=/tmp/testing.file state=absent"
```
загрузить файл из web
```bash
ansible all -m get_url -a "url=https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.9.0-amd64-netinst.iso dest=/tmp" -b
```
Установить пакет RHEL системы
```bash
ansible all -m yum -a "name=sudo state=installed"
```
Установить пакет DEB системы
```bash
ansible all -m ansible.builtin.apt -a "name=apache2 state=latest" -b
```
Проверить доступ до веба
```bash
ansible all -m uri -a "url=https://hub.docker.com"
```
Установить apache2 RHEL
```bash
ansible all -m ansible.builtin.apt -a "name=httpd"
```
Установить apache2 DEB
```bash
ansible all -m ansible.builtin.apt -a "name=apache2 state=latest" -b
```
активировать службу веб и поставить в автозапуск RHEL
```bash
ansible all -m service -a "name=httpd state=started enabled=yes" -b
```
Активировать службу веб и поставить в автозапуск DEB 
```bash
ansible all -m service -a "name=apache2 state=started enabled=yes" -b
```
Поиск модуля:
```bash
ansible-doc -l | grep apt
```

## Полезная информация
Посмотреть информацию о модуле ansible-doc ansible.builtin.apt
```bash
ansible-doc ansible.builtin.apt
```
Или можно посмотреть в браузере, напр https://docs.ansible.com/ansible/2.8/modules/file_module.html#file-module
Посмотреть hosts со всеми подключенными переменными, группами и т.д.
```bash
ansible-inventory --list
```