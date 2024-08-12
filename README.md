# Установка Wazuh сервиса на AlmaLinux 9

## Запуск через Ansible playbook

### 1. Установка ansible (AlmaLinux)

```
# Almalinux
sudo dnf install ansible -y
```
### 2. Скорректировать файл inventory (./ansible/inventory.yml)
   - Указать ip адреса хостов
   - Указать путь к ключам ssh
   - Сменить логин и пароль учётной записи, по которой будет подключаться ansible
---
### ! Важно !
Не менять названия хостов в inventory, т.к. к ним привязано исполнение ролей

---

### 3. Выполнить запуск playbook

```
ansible-playbook ./ansible/install_wazuh.yml -i inventory.yml -e manager_ip=ip_сервера_wazuh --ask-vault-password
```
