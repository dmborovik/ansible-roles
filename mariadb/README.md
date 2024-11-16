mariadb
=========

Установка БД MariaDB

Требования
------------

- Almalinux 9

Переменные
--------------

version_MariaDB - Версия БД.

mysql_root_pass - Пароль для пользователя root БД.

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: mariadb, version_MariaDB: Версия MariaDB }
