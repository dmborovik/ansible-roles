Установка LSPHP
===============

Требования
------------

- **Ubuntu**: 24

Переменные
--------------

- *lsphp_version:* версия lsphp
- *lsphp_modules:* необходимые для установки модули

Зависимости
------------

Пример использования
--------------------

    - hosts: servers
      roles:
        - { role: lsphp, lsphp_version: 83, lsphp_modules: "{{ php_module }}" }
        