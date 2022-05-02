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

_**user deletion**_

with userdel command you can dlelete a user

```bash
sudo userdel -f dodo
```
**Set Password**

```bash
sudo passwd dodo
```

_**custom shell assign for users**_

_**in centos**_



