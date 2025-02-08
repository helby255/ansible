# ansible
Простейшая конфигурация для работы с 3 тестовыми ВМ.
```bash
ansible testing -m ping
```
```bash
ansible all -m shell -a "uptime"
```
```bash
ansible all -m shell -a "free -h"
```
```bash
ansible all -m shell -a "df -Th"
```