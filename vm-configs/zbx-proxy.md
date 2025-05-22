#  ВМ: Zabbix Proxy (zbx-proxy)

##  Общая информация

- Hostname: `zbx-proxy`
- IP: `10.0.2.13`
- OS: Ubuntu 22.04 (cloud-init)
- Префикс имени: `vm-ubu22-zbx-proxy-01`
- VMID: `1203`

##  Ресурсы

- CPU: 1 vCPU
- RAM: 1024 MB
- Disk: 4 GB

##  Сетевые настройки

- Bridge: `vmbr1`
- IP: `10.0.2.13/24`
- Gateway: `10.0.2.1`
- DNS: `10.0.2.124`
- Domain: `reu-syslab.dev`

##  Доступ

- Cloud-init: 
- SSH по ключу: 
- QEMU Agent: 

##  Статус

- [ ] ВМ создана из шаблона `9401`
- [ ] Установлен Zabbix Proxy
- [ ] Проверено соединение с `zbx-server`