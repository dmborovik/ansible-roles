Установка PHP
=============

Требования
------------

- **Almalinux**: 8/9
- **Arch**
- **Ubuntu**: 22

Переменные
--------------

- *php_version:* версия php
- *php_modules:* необходимые для установки модули

**Параметры php.ini.**

- *php_memory_limit:*  лимит памяти PHP

Зависимости
------------

Пример использования
--------------------

    - hosts: servers
      roles:
        - { role: php, php_version: 8.3, php_modules: "{{ php_module }}", php_memory_limit: 512M  }
