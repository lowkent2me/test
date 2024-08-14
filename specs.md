**Тестовое задание для DevOps-инженера**

**Цель:**

Развернуть и настроить систему мониторинга и безопасности Wazuh, используя Ansible роли для автоматизации процесса.

**Описание задания:**

1. **Создание виртуальных машин:**
    - Поднимите две виртуальные машины с использованием AlmaLinux 9. Вы можете использовать Vagrant, VirtualBox, VMware или любые другие инструменты виртуализации.
1. **Подготовка Ansible роли:**
    - Разработайте Ansible роль, которая включает следующие задачи:
        - Деплой и обновление конфигураций Wazuh-server в режиме single-node в контейнере Docker.
        - Деплой Wazuh-менеджера на другую виртуальную машину, но вне контейнера Docker.
1. **Проверка результата:**
    - Убедитесь, что Wazuh-server и Wazuh-менеджер корректно работают после выполнения Ansible роли.
1. **Доступ к Wazuh из внешней сети:**
    - Настройте доступ к Wazuh из другой сети. Например, вы можете использовать Ngrok для проброса порта и обеспечения удаленного доступа.
1. **Отправка данных агентом:**
    - Настройте Wazuh-агент на одной из виртуальных машин так, чтобы он отправлял данные на развернутый Wazuh-сервер.
1. **Идемпотентность роли:**
    - Убедитесь, что ваша Ansible роль является идемпотентной, то есть повторный запуск роли не должен вносить изменений, если текущая конфигурация уже соответствует заданной.

**Ожидаемые результаты:**

1. **Виртуальные машины:**
    - Две виртуальные машины с установленным AlmaLinux 9.
1. **Ansible роль:**
    - Репозиторий с Ansible ролью, включающей все необходимые задачи для деплоя Wazuh-server и Wazuh-менеджера, а также конфигурации агента.
    - Роль должна быть документирована и содержать инструкции по запуску.
1. **Работающая система Wazuh:**
    - Wazuh-server в Docker-контейнере на одной виртуальной машине.
    - Wazuh-менеджер, развернутый вне Docker, на другой виртуальной машине.
    - Wazuh-агент, отправляющий данные на Wazuh-сервер.
1. **Доступность из внешней сети:**
    - Настроенный доступ к Wazuh через Ngrok или аналогичный инструмент.

**Проверка:**

- Убедитесь, что все шаги выполнены корректно.
- Проверьте, что Ansible роль является идемпотентной.
- Убедитесь, что Wazuh-агент успешно отправляет данные на сервер.
- Подтвердите доступность Wazuh из внешней сети.

**Дедлайн:**

Пожалуйста, завершите задание в течение 4 дней.

**Оценка:**

Работа будет оцениваться по следующим критериям:

- Полнота выполнения задания.
- Идемпотентность Ansible роли.
- Корректность и стабильность работы развернутых компонентов.
- Документация и удобство использования роли.


-------------------------------