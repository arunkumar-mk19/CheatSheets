## General Linux commands

### 1. Change user group of a folder
---
`sudo chown -R username:usergroup folder/file`

example: 

```bash
sudo chown -R ec2-user:apache html
```

### 2. Check disk space
---
To check all disk space:
```shell
df -H
```

To check the folder size in human readable format:
```shell
du -sh directory_name
```

### 3. Zip a folder
---
Create a zip folder:
```bash
zip -r <output_file_name.zip> <folder_1> <folder_2> ... <folder_n>
```

Zip everything in current directory
```bash
zip -r <output_file_name.zip> .
```

Recursively zip current directory and all contents – excluding more than one subdirectory
```sh
zip -r k12clips_live_v1_backup\(10_10_2022\).zip . -x phpMyAdmin/\* backup/\* public/zip_uploads/\*
```
### 4. Copy modified files path in Git Repository
---
Code to copy modified files path in git repository.

Windows power shell command:
```shell
git diff --name-only --diff-filter=M | Set-Clipboard
```

Linux command:
```shell
git diff --name-only --diff-filter=M | xargs -I {} echo {} | xargs echo | xclip -selection clipboard
```

### 5. Copy file from local to server
---
Copying a file from local drive to ec2 server using terminal

```shell
pscp -i aws-private-key-file-path local-filepath username@ipaddress:server-file-path
```

Example:
```Shell
pscp -i C:\Users\ssh\private.ppk E:\Projects\vendor-test.zip ec2-user@3.2.1.5:/var/www/html/dir
```