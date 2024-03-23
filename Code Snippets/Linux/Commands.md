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