### 1. (.gitignore)
```
.gitignore
folder/<file-name>
folder/*
folder/subfolder/<file-name>
folder/sub-folder/*

*.log  # Ignore all .log files
*      # Ignore everything
!<file-name> # Except <file-name>
!folder      # Except folder
```

```sh
git rm --cached <file-name>
git rm -r cached .
fir ls-files
```
