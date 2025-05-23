#  Установка Zabbix Full Stand (ручной сценарий)

Документация процесса установки Zabbix Server, PostgreSQL и Frontend в разнесённой архитектуре. Актуально для проекта `reu-syslab.dev`. Версия Zabbix: 7.2.

---

##  1. PostgreSQL (zbx-db, IP: 10.0.2.12)

### Установка:

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib -y
```

### Создание пользователя и базы данных:

```bash
sudo -u postgres createuser --pwprompt zabbix
# (ввести надёжный пароль вручную)

sudo -u postgres createdb -O zabbix zabbix
```

### Настройка доступа:

Файл: `/etc/postgresql/14/main/pg_hba.conf`

```conf
host    zabbix    zabbix    10.0.2.11/32    scram-sha-256
host    zabbix    zabbix    10.0.2.14/32    scram-sha-256
```

Файл: `/etc/postgresql/14/main/postgresql.conf`

```conf
listen_addresses = '*'
```

Перезапуск:

```bash
sudo systemctl restart postgresql
```

---

##  2. Zabbix Server (zbx-server, IP: 10.0.2.11)

### Добавление репозитория:

```bash
wget https://repo.zabbix.com/zabbix/7.2/release/ubuntu/pool/main/z/zabbix-release/zabbix-release_7.2-1+ubuntu22.04_all.deb
sudo dpkg -i zabbix-release_7.2-1+ubuntu22.04_all.deb
sudo apt update
```

### Установка компонентов:

```bash
sudo apt install zabbix-server-pgsql zabbix-agent2 zabbix-sql-scripts postgresql-client -y
```

### Инициализация базы данных:

```bash
zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | psql -U zabbix -d zabbix -h 10.0.2.12
```

(ввести пароль пользователя `zabbix`)

### Настройка Zabbix Server:

Файл: `/etc/zabbix/zabbix_server.conf`

```conf
DBHost=10.0.2.12
DBName=zabbix
DBUser=zabbix
DBPassword=********
```

### Запуск сервиса:

```bash
sudo systemctl restart zabbix-server
sudo systemctl enable zabbix-server
```

---

##  3. Zabbix Frontend (zbx-frontend, IP: 10.0.2.14)

### Установка:

```bash
sudo apt install zabbix-frontend-php zabbix-nginx-conf php8.1-pgsql -y
```

### Конфиг nginx:

Файл: `/etc/zabbix/nginx.conf`

```nginx
server {
    listen          8080;
    server_name     localhost;

    root    /usr/share/zabbix;

    index           index.php;

    location ~ \.php$ {
        fastcgi_pass   unix:/run/php/php8.1-fpm.sock;
        ...
    }
}
```

```bash
sudo systemctl restart nginx
sudo systemctl restart php8.1-fpm
```

### Конфиг Zabbix GUI:

Файл: `/etc/zabbix/web/zabbix.conf.php`

```php
$ZBX_SERVER      = '10.0.2.11';
$ZBX_SERVER_NAME = 'Zabbix Core';
$DB['SERVER']    = '10.0.2.12';
$DB['PORT']      = '5432';
$DB['DATABASE']  = 'zabbix';
$DB['USER']      = 'zabbix';
$DB['PASSWORD']  = '*******';
$DB['ENCRYPTION'] = false;
```

---

##  GUI доступен

Открыть: [http://10.0.2.14:8080](http://10.0.2.14:8080)  
Login: `Admin`  
Password: `zabbix`

(рекомендуется сменить пароль после первого входа)

---