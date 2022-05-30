postgresql-installation-and-configuration.md
---

|server|service|
|---|---|
|ubuntu| postgresql|


_installation_

```bash
sudo apt update 
sudo apt install postgresql postgresql-contrib -y

```
---

_To check running status_

```bash

sudo systemctl status postgresql.service

```
```bash

sudo ss -tulpn | grep 5432

```
---

_login commands_

login Default user 

```bash
sudo -u postgres psql
```
To remote login

```bash

psql -h <host> -p <port> -U <username> <database>

```
---

_database creation_


```bash

sudo -u postgres createdb dodo

or

createdb dodo;

```
---

_user creation and role assignment_

TO create the new user 

```bash
sudo -u postgres createuser --interactive
#Enter name of role to add: dodo
#Shall the new role be a superuser? (y/n) n
#Shall the new role be allowed to create databases? (y/n) n
#Shall the new role be allowed to create more new roles? (y/n) n

```
change superuser role

```bash
ALTER USER dodo WITH SUPERUSER;
```
---

_backup_

```bash

 pg_dump db1 > db1.sql

```
_RemoteBackup_

```bash
pg_dump -U tecmint -h <host> -p 5432 db1 > db1.sql
```
---

_restore_


```bash

 pg tecmintdb < tecmintdb.sql
```


replication


```back


```
