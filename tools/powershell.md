# Powershell cheatsheet
## Resolve-DnsName
what does this actually do?
```powershell
Resolve-DnsName -Name <dns>
```
## nslookup
```powershell
nslookup <ip or address>
```
Test-NetConnection
neat little "ping-like" tool to test connectability to a specific port:
```Powershell
Test-NetConnection <ip or address> -p <port>
```
