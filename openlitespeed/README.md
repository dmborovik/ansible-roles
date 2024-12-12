Установка OpenLiteSpeed
===============

Установка OpenLiteSpeed

Требования
------------

- **Ubuntu:** 24

Переменные
--------------

- ***listener_port:*** Установка порта Listener по умолчанию

Зависимости
------------

Пример использования
--------------------

    - hosts: servers
      roles:
        - {role: openlitespeed, listener_port: 80}
