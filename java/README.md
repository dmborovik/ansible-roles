java
=========

Установка java

Требования
------------

- **Almalinux**: 8|9
- **Ubuntu**: 24.04
- **CentOS Stream:** 9

Переменные
--------------

- *java_version*: версия java

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: java, java_version: 21 }
