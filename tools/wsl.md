# WSL - Windows Subsystem for Linux
## fix DNS-resolve-Issue
with WSL 2 comes the annoying issue, that after the installation or a reboot `/etc/resolv.conf`gets overwritten. To fix the file do the following:
```bash
sudo nano /etc/resolve.conf
```
edit the file to this:
```
nameserver 8.8.8.8
nameserver 4.4.4.4
```
Links:
- https://askubuntu.com/questions/1347712/make-etc-resolv-conf-changes-permanent-in-wsl-2