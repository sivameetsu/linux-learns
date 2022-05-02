## user management
User management includes everything from creating a user to deleting a user on your system.

**root**

The root user is the superuser and have all the powers for creating a user, deleting a user and can even login with the other user's account. The root user always has userid 0.

**User Creation**

With useradd commands you can add a user.

```bash
useradd dodo
```
**User Deletion**

with userdel command you can dlelete a user

```bash
sudo userdel -f username
```
**Set Password**

```bash
sudo passwd username
```
