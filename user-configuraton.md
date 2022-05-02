## user management
User management includes everything from creating a user to deleting a user on your system.

**root**

The root user is the superuser and have all the powers for creating a user, deleting a user and can even login with the other user's account. The root user always has userid 0.

**User Creation**

With useradd commands you can add a user.

```bash
useradd
```
 
![image](https://user-images.githubusercontent.com/98270930/166136960-cdd3b639-421f-47b6-a574-614c35a65bf1.png)


![image](https://user-images.githubusercontent.com/98270930/166136972-6e8f84cb-53ab-4a5b-bad5-3756365263e5.png)

**User Deletion**

with userdel command you can dlelete a user

```bash
sudo userdel -f username
```
**Set Password**

```bash
sudo passwd username
```
