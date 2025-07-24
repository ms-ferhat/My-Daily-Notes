### File, Permission and Timestamps

to investigate files and their permission, we could used both `ls -al` for specific __folder__ or `find` for specific __user__.

```
ls -al                                ## list all file in folder wiht permission info

find / -user (user-name) 2>/dev/null  ## list all file for user-name

find / -group GROUPNAME 2>/dev/null   ## Retrieve a list of files and directories owned by a specific group.

find / -perm -o+w 2>/dev/null         ## Retrieve a list of all world-writable files and directories.

find / -type f -cmin -5 2>/dev/null   ## Retrieve a list of files created or changed within the last five minutes
```


you need to check __metadata__, __hash__ and __Timestamps__ of any file you think it was suspicion.

```
exiftool file-name    ## to show file metadata

sha1sum file-name     ## to calculate SHA 1 hash for file

stat file-name        ## to show file's timestamps
```




