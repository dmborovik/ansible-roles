java
=========

Установка java

Требования
------------

- Ubuntu 24.04

Переменные
--------------

- java_version: Версия java

Пример плэйбука
----------------

    - hosts: servers
      roles:
         - { role: java, java_version: 21 }
