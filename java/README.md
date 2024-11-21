java
=========

Установка java

Требования
------------

- **Almalinux**: 9

- **Ubuntu**:    24.04

Переменные
--------------

- *java_version*: версия java

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: java, java_version: 21 }
