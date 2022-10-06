# nala
## what it is?
nala is a really nice replacement for apt/apt-get. Under the hood it uses apt, but it has a totally superior user interface and adds functionality to view the update history, auto-purge and auto-remove packages that are no longer needed. On top of that it has a neat feature to customize the used mirrors based on a integrated speed test, which can speed up the updating-progress. 

Basically everyone how maintains a ubuntu or debian linux should use apt only once: to install nala and that's it!

## how to install?
1. add the *Volian Scar* repositories to your system: 
```shell
echo "deb [arch=amd64,arm64,armhf] http://deb.volian.org/volian/ scar main" | sudo tee /etc/apt/sources.list.d/volian-archive-scar-unstable.list
```
2. add the GPG key for verification:
```shell
wget -qO - https://deb.volian.org/volian/scar.key | sudo tee /etc/apt/trusted.gpg.d/volian-archive-scar-unstable.gpg > /dev/null
```
3. install nala using apt (for the last time 😆)

On "old" Ubuntu (21.x or older) or Debian Stable you need to install nala-legacy: 
```shell
sudo apt update && sudo apt install nala-legacy
```
On Ubuntu 22.04/Debian you can install the standard nala-package:
```bash
sudo apt update && sudo apt install nala
```

## command reference
| command | what ist does |
|---|---|
| `nala update` | update package list |
| `nala upgrade` | update package list and upgrade the system |
| `nala install --update <name>` | install packages and update the package list before |
| `nala list -i` | list installed packages |
| `nala history` | show transaction history |
| `nala history info [ID]` | show information about a specific transaction. "last" can be used as ID |
| `nala history undo [ID]` | undo the specific transaction |

## links
- https://gitlab.com/volian/nala
- https://trendoceans.com/nala-package-manager/