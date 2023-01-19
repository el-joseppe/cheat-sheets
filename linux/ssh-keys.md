# ssh-keys
## enable ssh-access without password
1. generate ssh-key if necessary:
```shell
ssh-keygen
```
2. copy key to the remote system, you want to access without password:
```shell
ssh-copy-id user@hostname
```
or on powershell:
```powershell
type $env:USERPROFILE\.ssh\id_rsa.pub | ssh user@hostname "cat >> .ssh/authorized_keys"
```
3. test
```shell
ssh user@hostname
```

see: 
- https://linuxconfig.org/passwordless-ssh
- https://www.simplified.guide/ssh/copy-public-key

## manage connections with ssh-config and sshto
