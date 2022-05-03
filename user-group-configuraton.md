## user management
User management includes everything from creating a user to deleting a user on your system.

_**Requirmenets**_

|users | state |
|---|---|
| root | default user |
| dodo | custom user |

_**root user**_

The root user is the `superuse`r and have all the permissions for creating a user, deleting a user and can even login with the other user's account. The root user always has userid 0. this user can be control entire systes.

_**custom user creation process**_

_**in ubuntu**_

```bash
useradd dodo
```
In this command create /etc/passwd, /etc/shadow, /etc/group and /etc/gshadow files for the newly created user accounts.

_**user deletion**_

with userdel command you can dlelete a user

```bash
sudo userdel -f dodo
```
**Set Password**

```bash
sudo passwd dodo
```
**To check user creation**

```bash
cat /etc/passwd
```
**Group Creation Group**

```bash 
groupadd Group-Name
```
The command adds an entry for the new group to the /etc/group and /etc/gshadow files.

```bash
groupadd -f mygroup
```

Group add with specify Group ID
```bash
groupadd -g 1010 mygroup
```
to view and verify the GroupID use this command

```bash
getent group | grep mygroup
```
group Create with Password use this command

```bash
groupadd -p grouppassword mygroup
```





_**custom shell assign for users**_

_**in centos**_



