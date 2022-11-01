# enable ssh-access without password
1. generate ssh-key if necessary:
```shell
ssh-keygen
```
2. copy key to the remote system, you want to access without password:
```shell
ssh-copy-id user@hostname
```
3. test
```shell
ssh user@hostname
```

see: 
- https://linuxconfig.org/passwordless-ssh