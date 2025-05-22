#  ВМ: Zabbix Server (zbx-server)

##  Общая информация

- Hostname: `zbx-server`
- IP: `10.0.2.11`
- OS: Ubuntu 22.04 (cloud-init)
- Префикс имени: `vm-ubu22-zbx-srv-01`
- VMID: `1201`

##  Ресурсы

- CPU: 2 vCPU
- RAM: 2048 MB
- Disk: 8 GB (VirtIO SCSI)

##  Сетевые настройки

- Bridge: `vmbr1`
- IP: `10.0.2.11/24`
- Gateway: `10.0.2.1`
- DNS: `10.0.2.124`
- Domain: `reu-syslab.dev`

##  Доступ

- Cloud-init: 
- SSH по ключу: 
- QEMU Agent: 

##  Статус

- [x] ВМ создана и клонирована из шаблона `9300`
- [ ] Установлен Zabbix Server
- [ ] Проверена связь с `zbx-db`
- [ ] Подключена к frontend и proxy