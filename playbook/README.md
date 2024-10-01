## Ansible Playbook для запуска Clickhouse + Vector + lighthouse

### Особоенности:
* Установка и настройка тестовой конфигурации Clickhouse, Vector 
* Гибкая настройка конфига Vector посредством Jinja template
* если использовать версию Vector >= 0.41.1 для вм нужна версия CentOS >=8 т.к. библиотека libc-2.18.so в CentOS 7 не поддерживается 
---
## Первоначальная настройка 
Заполните инвентарный файл **[inventory/prod.yml]**
```YML
ansible_host: ip
ansible_ssh_user: user
ansible_ssh_private_key_file: PRIVATE_KEY_FILE
```

Укажите необходимую версию clickhouse **[group_vars/clickhouse/vars.yml]**, например "22.3.3.44"
```YML
clickhouse_version: 22.3.3.44
```
Укажите необходимую версию vector **[group_vars/vector/vars.yml]**, например "0.41.1"
```YML
vector_version: 0.41.1
```
В файле **[lighthouse/vars.yml]** укажите IP\порт, который будет слушать веб-сервер
```YML
nginx_address: 0.0.0.0:8080
```
В файле **[vector/vars.yml]** укажите IP на котором будет запущен clickhouse, если сервис будет запущен на одной инстансе, то оставьте настройку как есть
```YML
endpoint: http://localhost:8123
```

## Play

#
    ansible-playbook site.yml -i inventory/prod.yml
**Note**: После выполнения playbook Vector сразу начнет писать лог в БД

## Документация 

**[What Is ClickHouse](https://clickhouse.com/docs/en/intro)**

**[Vector - A lightweight, ultra-fast tool for building observability pipelines](https://vector.dev/)**
