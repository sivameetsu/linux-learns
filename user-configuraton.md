## user management
User management includes everything from creating a user to deleting a user on your system.

**Process flow to create the users**

|users | state |
|---|---|
| root | default user |
| dodo | custom user |

**root user**

The root user is the `superuse`r and have all the permissions for creating a user, deleting a user and can even login with the other user's account. The root user always has userid 0. this user can be control entire systes.

**user Creation process**

With useradd commands you can add a user.

```bash
useradd dodo
```
**User Deletion**

with userdel command you can dlelete a user

```bash
sudo userdel -f dodo
```
**Set Password**

```bash
sudo passwd dodo
```
