#  Proxmox Templates — Zabbix Full Stand

Описание шаблонов виртуальных машин, используемых для быстрого клонирования в рамках проекта.

---

##  tmpl-ubu22-core-fixed (VMID 9300)

**Назначение:** продакшн-сервисы (Zabbix, DNS, PostgreSQL)

- ОС: Ubuntu 22.04 (cloud-init)
- CPU: 2 vCPU
- RAM: 2048 MB
- Disk: 8 GB (VirtIO SCSI)
- Сеть: VirtIO, bridge=vmbr1
- Cloud-init: 
- QEMU Agent: 

---

##  tmpl-ubu22-dev-upd (VMID 9401)

**Назначение:** dev/тестовые среды, Docker, CI/CD

- ОС: Ubuntu 22.04 (cloud-init)
- CPU: 1 vCPU
- RAM: 2048 MB
- Disk: 8 GB (VirtIO SCSI)
- Сеть: VirtIO, bridge=vmbr1
- Cloud-init: 
- QEMU Agent: 

---

> Для использования шаблонов клонируйте их через Proxmox GUI или CLI:

```bash
qm clone 9300 <VMID> --name <имя> --full
qm set <VMID> --ipconfig0 ip=10.0.2.X/24,gw=10.0.2.1
```