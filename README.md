# Задание 1
Разработайте ansible, который запускает докеризованное веб-приложение (nginx, php, mysql) с помощью docker-compose на удаленном сервере.
Сценарий должен:
1. Дистрибьютить необходимые для работы файлы
2. Генерировать файл конфигурации для nginx и при необходимости перезапустить его.

Результатом заполнения технического задания является:
1. Ansible playbook (вместе с ролями и/или файлом с зависимостями, необходимыми шаблонами);
2. docker-compose.yml
3. Dockerfile

# Решение

В качестве веб приложения решено использовать Zabbix, т.к. оно соответсвует всем требованиям (PHP, Nginx, Mysql)

1. Дистрибьюция файлов происходит в роли install_zabbix. Файл systemd юнита передаётся в директорию обработки daemon'ов.
2. Под генерацией я понял использование шаблона конфигурационного файла nginx. Этот файл и другие шаблоны находятся в директориях template ansible ролей

# Как запустить сервис

Есть два способа запустить сервис zabbix:
- Через docker compose
- Через установку, описанную в ansible playbook'е

# Запуск через docker compose

Чтобы запустит сервис zabbix через docker compose, необходимо установить Docker Engine и плагин docker compose на хост-машине

```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

Далее необходимо запустить docker compose

```
docker compose -f /path/to/docker/compose/file.yaml up -d
```

Сервис запущен. Можно перейти по http://localhost для входа на портал сервиса

# Запуск через Ansible playbook

Установка ansible (Ubuntu)

```
# ubuntu
sudo apt-get install ansible
```

Выполнить запуск playbook

```
ansible-playbook install-playbook.yml -i inventory.ini -e "target=localhost" -K -v
```
