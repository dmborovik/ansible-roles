mariadb
=========

Установка БД MariaDB

Требования
------------

- **Almalinux:** 8/9
- **Arch**

Переменные
--------------

- *version_MariaDB:* Версия БД.

- *mysql_root_pass:* Пароль для пользователя root БД.

- *secure_install:* Произвести настройки безопасности (True/False)

- *create_db:* Создать ли базу (True/False)

- *create_user:* Создание пользователя (True/False)

- *db_name:* имя базы

- *db_user:* имя пользователя БД

- *db_user_pass:* пароль пользователя БД

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: mariadb, version_MariaDB: 10.5, create_db: True, create_user: True }
