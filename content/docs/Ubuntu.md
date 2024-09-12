---
title: Ubuntu
type: docs
prev: docs/SQL
next: docs/
---

### Mistake in sudoers or similar?
1. Reboot and access GRUB menu using `ESC`/`SHIFT` at boot time
2. Go into `Advanced Options for Ubuntu`
3. Choose a `Recovery Mode` option
4. Select `root` to `Drop to root shell prompt`
5. `mount -o remount,rw /`
6. Fix your sudoers issue or remove if `/etc/sudoers.d/my_sudoers_file`
7. `reboot`

### Forgotten `root` password or not set?
1. Reboot and access GRUB menu using `ESC`/`SHIFT` at boot time
2. Highlight your GRUB entry (usually first one)
3. Press `e` to edit boot params
4. At end of line beginning with `linux` type: `init=/bin/bash`
5. Press `CTRL + X` or `F10` to enter single-user mode
6. Run `mount -o remount,rw /` to remount the FS in RW
7. Change/Set the password for the `root` user using: `passwd`
8. Reboot system forcefully or run: `exec /sbin/init`

#### Change TZ to London
```
sudo ln -sf /usr/share/zoneinfo/Europe/London /etc/localtime
```
