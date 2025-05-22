#  ВМ: Zabbix Frontend (zbx-frontend)

##  Общая информация

- Hostname: `zbx-frontend`
- IP: `10.0.2.14`
- OS: Ubuntu 22.04 (cloud-init)
- Префикс имени: `vm-ubu22-zbx-fe-01`
- VMID: `1204`

##  Ресурсы

- CPU: 1 vCPU
- RAM: 1024 MB
- Disk: 4 GB

##  Сетевые настройки

- Bridge: `vmbr1`
- IP: `10.0.2.14/24`
- Gateway: `10.0.2.1`
- DNS: `10.0.2.124`
- Domain: `reu-syslab.dev`

##  Доступ

- Cloud-init: 
- SSH по ключу: 
- QEMU Agent: 

##  Статус

- [ ] ВМ создана из шаблона `9401`
- [ ] Установлен NGINX + PHP-FPM + Zabbix Frontend
- [ ] GUI доступно на `http://10.0.2.14`