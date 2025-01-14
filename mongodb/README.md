mongodb
=========

Установка БД MongoDB

Требования
------------

- **AlmaLinux:** 8
- **Debian:** 12

Переменные
--------------

- *version_MongoDB:* Версия БД.

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: mongodb, version_mongodb: 8.0 }
