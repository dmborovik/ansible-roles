# Apache role

Роль автоматически определяет семейство ОС и устанавливает нужный пакет и сервис Apache.

## Поддерживаемые ОС

Роль протестирована на следующих ОС (на основе `ansible_os_family`):

- **RedHat**:
  - AlmaLinux: 9, 10
  - CentOS Stream: 9, 10
- **Debian**:
  - Debian: 12
  - Ubuntu: 22.04
- **Archlinux**:
  - Arch Linux (rolling release)

Другие версии или дистрибутивы могут работать, но не были протестированы.

## Что делает эта роль

- Устанавливает Apache, используя пакетный менеджер ( через `apt`, `dnf`, `pacman`) в зависимости от ОС;
- Гарантирует, что сервис Apache **запущен** и **включен в автозагрузку**;
- Проверяет доступность порта `80` (настраиваемый через `apache_port`);
- Проверяет корректность конфигурации Apache перед перезапуском.
- Использует централизованную логику запуска сервиса в `main.yaml` для управления всеми ОС.

## Требования

- Ansible версии 2.9 или выше
- Права суперпользоватля (`become: true`) для установки пакетов и управления сервисами.
- Установленные пакетные менеджеры: `apt` (Debian/Ubuntu), `dnf` (AlmaLinux/CentOS Stream), `pacman` (Arch Linux)

## Переменные по умолчанию

Переменные определены в `defaults/main.yaml` и `vars/main.yaml` и зависят от семейства ОС (`ansible_os_family`):

```yaml
apache_package_name: 
  redhat: httpd
  debian: apache2
  archlinux: apache
apache_service_name:
  redhat: httpd
  debian: apache2
  archlinux: apache
apache_ctl_command:
  redhat: httpd -t
  debian: apache2ctl -t
  archlinux: apachectl -t
apache_port: 80
```

Вы можете переопределить эти переменные в вашем playbook'е или `group_vars`.

## Использование

Пример playbook'а:

```yaml
- hosts: webservers
  become: true
  roles:
    - apache
```

## Теги

Роль поддерживает следующие теги для выборочного выполнения задач:

- `install`: Устанавливает пакет Apache
- `service`: Управляет запуском и автозагрузкой сервиса.
- `config` : Проверяет конфигурацию Apache.

Пример: `ansible-playbook -t install playbook.yml`

## Тестирование и отладка

- Используйте `ansible-playbook --check` для проверки выполнения без изменений.
- Если Apache не отвечает на порт 80, проверьте:
  - Статус сервиса: `systemctl status {{ apache_servicre_name }}`
  - Доступность порта: `netstat -tuln | grep 80`
  - Логи Apache: `/var/log/apache2/error.log` (Debian/Ubuntu) или `/var/log/httpd/error_log` (RedHat).
- Для проверки конфигурации вручную выполните: `{{ apache_ctl_command }}`.

## Лицензия

Роль распространяется под лицензией MIT. См. файл LICENSE для подробностей.

## Автор

Dmitry Borovik
