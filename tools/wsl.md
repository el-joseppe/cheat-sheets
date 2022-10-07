# WSL - Windows Subsystem for Linux
## what it is?
## command reference
### list available distributions
```powershell
wsl --list --online
```
### install a distribution
```powershell
wsl --install -d <distibution>
```
### list installed distributions
```powershell
wsl -l -v
```
### start a specific distribution
```powershell
wsl -d <name>
```
### stop the running distribution
```powershell
wsl --shutdown
```
## Issues
### fix DNS-resolve-Issue
with WSL 2 comes the annoying issue, that after the installation or a reboot `/etc/resolv.conf`gets overwritten. To fix the file do the following:
```bash
sudo nano /etc/resolve.conf
```
edit the file to this:
```
nameserver 8.8.8.8
nameserver 4.4.4.4
```
see:
- https://askubuntu.com/questions/1347712/make-etc-resolv-conf-changes-permanent-in-wsl-2
- https://adamtheautomator.com/windows-subsystem-for-linux/