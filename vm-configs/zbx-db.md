#  ВМ: Zabbix Database (zbx-db)

##  Общая информация

- Hostname: `zbx-db`
- IP: `10.0.2.12`
- OS: Ubuntu 22.04 (cloud-init)
- Префикс имени: `vm-ubu22-zbx-db-01`
- VMID: `1202`

##  Ресурсы

- CPU: 2 vCPU
- RAM: 2048 MB
- Disk: 8 GB

##  Сетевые настройки

- Bridge: `vmbr1`
- IP: `10.0.2.12/24`
- Gateway: `10.0.2.1`
- DNS: `10.0.2.124`
- Domain: `reu-syslab.dev`

##  Доступ

- Cloud-init: 
- SSH по ключу: 
- QEMU Agent: 

##  Статус

- [ ] ВМ создана из шаблона `9300`
- [ ] Установлена PostgreSQL
- [ ] Проверена связь с `zbx-server`