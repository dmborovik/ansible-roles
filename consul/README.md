# Ansible Role: Consul

Установка и настройка HashiCorp Consul в режиме сервера или клиента.

## 📦 Совместимость

- Поддерживаемая ОС:
  - AlmaLinux `8`|`9`
- Ansible >= 2.10

## 🚀 Особенности

- Установка конкретной версии Consul
- Работа как сервер или клиент
- Настраиваемый конфиг и systemd unit
- Проверка доступности через HTTP API
- Поддержка tag-ов для избирательного запуска задач

---

## 🔧 Переменные

### Основные

| Переменная              | Описание                                   | Значение по умолчанию     |
|-------------------------|--------------------------------------------|----------------------------|
| `datacenter`            | Название датацентра                        | `dev`                      |
| `consul_version`        | Версия Consul                              | `"1.15.4"`                 |
| `consul_user`           | Пользователь для запуска Consul            | `"consul"`                 |
| `consul_group`          | Группа для Consul                          | `"consul"`                 |
| `consul_config_dir`     | Путь до директории конфигурации            | `"/etc/consul.d"`          |
| `consul_data_dir`       | Путь до директории данных                  | `"/opt/consul"`            |
| `consul_bind_address`   | Адрес, на который биндимся                 | `"0.0.0.0"`                |
| `consul_client_address` | Адрес, с которого принимаем запросы        | `"127.0.0.1"`              |
| `consul_node_role`      | Роль ноды (`server` или `client`)          | `"server"`                 |
| `consul_command_args`   | Аргументы запуска (будут переданы в systemd unit) | `agent -config-dir=...` |

---

## 📦 Пример использования

```yaml
- hosts: consul_servers
  become: yes
  roles:
    - role: consul
      vars:
        datacenter: "prod"
        consul_version: "1.15.4"
        consul_node_role: "server"
