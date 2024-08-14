# Установка Wazuh сервиса на AlmaLinux 9

## Запуск через Ansible playbook

### 1. Установка ansible (AlmaLinux)

```
# Almalinux
sudo dnf install ansible -y
```

### 2. Установка комьюнити модуля docker_compose_v2
``` 
ansible-galaxy collection install community.docker
```

### 3. Скорректировать файл inventory (./ansible/inventory.yml)
   - Указать ip адреса хостов
   - Указать путь к ключам ssh
   - Сменить логин и пароль учётной записи, по которой будет подключаться ansible

### 4. Выполнить запуск playbook

```
ansible-playbook ./ansible/install_wazuh.yml -i inventory.yml --ask-vault-password
```
---
### ! Переменные !
Можно переопределить следующие переменные:

- manager_ip (обязательно) - ip адрес ВМ wazuh
- workdir - путь установки сервера wazuh (по умолчанию /opt/wazzuh/workdir)
- wzh-version - версия контейнера (по умолчанию 4.8.1)
- indexer-username - логин для входа в веб интерфейс (по умолчанию admin)
- indexer-password - пароль для входа в веб интерфейс (по умолчанию SecreetPassword)
- api-username - API login (по умолчанию wazuh-wui)
- api-password - API password (по умолчанию MyS3cr37P450r.*-)
- dashb-username - dashboard login (по умолчанию kibanaserver)
- dashb-password - dashboard password (по умолчанию kibanaserver)
- certgen-version - версия контейнера генерации сертификатов wazuh (по умолчанию 0.0.2)

```
#Запуск с переопределением переменных
ansible-playbook ./ansible/install_wazuh.yml -i inventory.yml --ask-vault-password --extra-vars "manager_ip=192.168.1.10 workdir=/opt/wazuh"
```
---