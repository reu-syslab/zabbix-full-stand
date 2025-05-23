# Zabbix Full Stand Setup

Полноценный учебный стенд для развертывания системы мониторинга Zabbix по всем правилам:

* **Zabbix Server** — основное ядро системы
* **PostgreSQL** — база данных (выбор из рекомендаций )
* **Zabbix Frontend** — веб-интерфейс
* **Zabbix Proxy** — для сбора данных с агентов

---

## Цель проекта

Создать развёрнутую архитектуру Zabbix на базе 4 отдельных виртуальных машин с чистым и масштабируемым подходом:

* По учебным практикам
* С возможностью автоматизации в будущем (Ansible/Terraform)
* Для отладки, экспериментов и изучения промышленных решений

---

## Почему так?

На воркшопе (Практикум) было объяснено:

> В продакшене Zabbix принято разносить компоненты: server, frontend, proxy и БД — на отдельные хосты. Это повышает отказоустойчивость и управляемость.

Также важно:

* **теги** и **алерты** настраивать через **шаблоны**, а не напрямую на хостах.
* начинать даже лабораторный стенд с «правильной архитектуры», чтобы в будущем не сталкиваться с масштабируемыми ограничениями.

---

## Структура проекта

```
.
├── ansible/ # (в будущем) автоматизация установки
├── docs/ # Документация проекта
│ └── architecture.md # Текущая архитектура Zabbix Full Stand
├── vm-configs/ # Конфигурации ВМ (по ролям)
├── templates.md # Список шаблонов Proxmox
├── CHANGELOG.md # История изменений и версий
├── .gitignore # Git-исключения
└── README.md # Описание проекта

```

---


---

##  План действий

- [x] Создать публичный репозиторий
- [x] Подготовить README
- [ ] Настроить базовые ВМ
- [ ] Разнести роли по компонентам
- [ ] Проверить сбор метрик
- [ ] Вынести конфигурации в Ansible (опционально)
- [ ] Подключить агентов и шаблоны

---

##  Автор

Рувен (reu-syslab) — учебный проект в рамках курса "Системный Администратор" и самостоятельного исследования Zabbix и архитектуры мониторинга.

---

**Любой может использовать, дополнять или предлагать улучшения — стенд открыт для обучения и роста.**

