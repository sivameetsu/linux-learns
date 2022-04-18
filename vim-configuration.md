## vim configuration

**What is Vim?**

Vim is an advanced and highly configurable text editor built to enable efficient text editing. Vim text editor is developed by Bram Moolenaar. It supports most file types and vim editor is also known as a programmer’s editor. We can use with its plugin based on our needs.

**Vim Installation on ubuntu:**

```bash
sudo apt-get install vim
```
## Create, save,exit Commands:
|S.No|Commands|Description|
|----|---------|-----------|
|1.| vim (filename)| To create vim a file and To open a existing vim file|
|2.|:q!|Exit vim without saving changes |
|3.|:wq|Save a file and exit.|
|4.|:x|will save the changes and exit.|
|5.|:w [newfilename]| rename an existing file|
|6.|u|undo|
|7.|Ctrl + r|redo|

## Copy, Paste, Cut commands:
|S.No|Commands|Description|
|----|---------|-----------|
|1.| yy| To copy an entire line, place the cursor at the beginning of the line and type.|
|2.|3yy|To copy three (3) lines, move the cursor from where you want to begin copying and type.|
|3.|dd|To cut the entire line in which the cursor is located type.|
|4.|3dd|To cut three (3) lines, starting from the one where the cursor is located use.|
|5.|d$|To cut everything right of the cursor to the end of the line use the command.|
|6.|p|To paste it.|
|7.|P|To add text before the cursor.|
|8.|d|d to delete (cut) the content.|
|9.|V|V (uppercase) to select the entire line.|
|10.|dd|delete the line.|
