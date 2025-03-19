Ansible Role: MariaDB
=========

Описание
--------

Данная Ansible роль устанавливает и настраивает MariaDB на серверах с дистрибутивами RHEL, Debian и Arch Linux. Роль также может выполнять базовую защиту сервера, создание базы данных и пользователя.

Поддерживаемые платформы
------------

- **Almalinux:** 8/9
- **Arch**
- **CentOS Stream:** 9
- **Debian:** 12
- **Ubuntu:** 22

Переменные роли
--------------

Все переменные хранятся в defaults/main.yml и могут быть переопределены в vars.yml или через командную строку.

Основные переменные
--------------------

```yaml
version_MariaDB: "11.4"  # Версия MariaDB
mysql_root_pass: "SuperSecretPass"  # Пароль root пользователя

secure_install: true  # Удалять анонимных пользователей и тестовую БД
create_db: false  # Создавать базу данных
create_user: false  # Создавать пользователя базы данных

db_name: "example_db"  # Имя БД
db_user: "example_user"  # Имя пользователя БД
db_user_pass: "ExamplePassword"  # Пароль пользователя БД

mysql_socket: >-
  {% if ansible_os_family == "RedHat" %}/var/lib/mysql/mysql.sock
  {% else %}/run/mysqld/mysqld.sock{% endif %}

```

Использование
-------------

**1.Включение роли в playbook.**
Добавьте роль в ваш `site.yml`:

  ```yaml
  - hosts: db_servers
    roles:
      - mariadb
  ```

**2.Переопределение переменных.**
Создайте `vars.yml` и укажите там свои значения:

```yaml
mysql_root_pass: "MySecurePassword"
create_db: true
create_user: true
db_name: "mydatabase"
db_user: "myuser"
db_user_pass: "mypassword"
```

Запуск плейбука с переопределением:

```bash
ansible-playbook site.yml -e @vars.yml
```

Безопасность
------------

Рекомендуется **не хранить пароли в открытом виде**. Используйте **Ansible Vault** для шифрования переменных:

```bash
ansible-vault encrypt vars.yml
ansible-playbook site.yml --ask-vault-pass
```
