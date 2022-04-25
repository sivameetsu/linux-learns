## find commands

### What is find commands?

- The Linux find command is one of the most important and frequently used command command-line utility in Unix-like operating systems. 

- The find command is used to search and **locate the list of files and directories** based on conditions you specify for files that match the arguments.

- Find command can be used in a variety of conditions like you can find files by **permissions, users, groups, file types, date, size** and other possible criteria.


### Part I: Basic Find Commands for Finding Files with Names

| Command | Description |Output|
| --- | --- |--|
| `find . -name one.txt` | Find all the files whose name is one.txt in a current working directory.|![image](https://user-images.githubusercontent.com/91359308/165037344-e6fa4bef-004e-428a-8ecb-09831e2e6a59.png)|
| `find /home -name one.txt` | Find all the files under /home directory with the name one.txt. |![image](https://user-images.githubusercontent.com/91359308/165037532-cc1c81e3-56b3-42ee-a1fd-0b3fcf2ccec0.png)|
| `find /home -iname one.txt` | Find all the files whose name is one.txt and contains both capital and small letters in /home directory. |![image](https://user-images.githubusercontent.com/91359308/165037815-c345be3f-367b-46d2-b3e9-f3ea4f0f2e55.png)|
| `find / -type d -name Tecmint` |Find all directories whose name is Tecmint in / directory.  |![image](https://user-images.githubusercontent.com/91359308/165038557-1baf31c1-aaf4-4d63-889d-1579b1f64e6d.png)|
| `find . -type f -name one.js` | Find all php files whose name is one.js in a current working directory.|![image](https://user-images.githubusercontent.com/91359308/165039513-43772280-c11e-47c0-9e4f-b968effc9c07.png)|
| `find . -type f -name "*.php"` | Find all php files in a directory. |![image](https://user-images.githubusercontent.com/91359308/165039847-25de6aef-2989-43fe-b41c-761720535546.png)|

| `find . -type f -perm 0777 -print` |Find all the files whose permissions are 777.  |
| `` |  |
| `` |  |

| `` |  |
| `` |  |
| `` |  |
| `` |  |
