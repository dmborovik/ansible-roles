mongodb
=========

Установка БД MongoDB

Требования
------------

- **Debian:** 12

Переменные
--------------

- *version_MongoDB:* Версия БД.

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: mongodb, version_mongodb: 8.0 }
