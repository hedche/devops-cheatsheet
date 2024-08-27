---
title: Bash
type: docs
prev: docs/Bash
next: docs/Docker
---

## sed
#### Against variables
```bash
sed ‘s/Hello/Hi/g’ <<< “$var”
```
#### Against file
```bash
sed ‘s/Hello/Hi/g’ -i /path/goes/here.txt`
```
#### Delete a line
```bash
sed ‘/pattern/d’
```
#### Replace with string
```bash
sed ‘s/pattern/string/g’
```

## grep
#### Find string in files and show filenames
```bash
grep -H 'my_string' /path/to/multiple/*/*/*
```

## tar
#### Compress
```bash
tar -cvzf archive_name.tar.gz directory
```
#### Uncompress
```bash
tar -xvzf archive_name.tar.gz -C /path/to/dest_dir
```

## File Descriptors
Suppress stdout + stderr:
```bash
ls non_existent_dir >/dev/null 2>&1` OR `ls non_existent_dir &>/dev/null
```

## Random
#### Run portion of Bash script as another user
```bash
if [[ $(id -u) -eq 0 ]]; then
  su - target_user -c "$(cat << 'EOF'
    # command1
    # command2
    EOF
  )"
else
  echo "Exiting as not root..."
fi
```
