# apache

Роль автоматически определяет семейство ОС и устанавливает нужный пакет и сервис.

## Поддерживаемые ОС

- **Almalinux:** `8`,`9`
- **Arch:**
- **CentOS Stream:** `9`,`10`
- **Debian:** `12`
- **Ubuntu:** `22.04`

## Что делает эта роль

- Устанавливает Apache в зависимости от ОС ( через `apt`, `dnf`, `pacman`);
- Гарантирует, что Apache-сервис **запущен** и **включен в автозагрузку**;
- Проверяет, что порт `80` доступен;
- Использует централизованную логику запуска сервиса в `main.yaml` ( а не в os-specific файлах).

## Переменные по умолчанию

```yaml
#defaults/main.yml
apache_service_name: "{{ 'apache2' if ansible_os_family == 'Debian' else 'httpd' }}"
```

Можно переопределить имя сервиса, если используется другой init-скрипт или имя пакета:

```yaml
apache_service_name: my-custom-apache
```

## Использование

Пример playbook'а:

```yaml
- hosts: webservers
  become: true
  roles:
    - apache
```

## Структура роли

```text
tasks/
├── main.yml           # Основная логика + запуск Apache
├── rhel.yaml          # Установка Apache на RHEL/AlmaLinux/CentOS
├── debian.yaml        # Установка Apache на Debian/Ubuntu
└── arch.yaml          # Установка Apache на Arch
defaults/
└── main.yml           # Значение apache_service_name
```

## Лицензия

MIT

## Автор

Dmitry Borovik
