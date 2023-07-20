# remove nag
```shell
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid sub)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service
```

This mod works on both PVE and PBS.
see: [link](https://i12bretro.github.io/tutorials/0446.html)

# dark mode
```shell
bash <(curl -s https://raw.githubusercontent.com/Weilbyte/PVEDiscordDark/master/PVEDiscordDark.sh ) install
```

This is obsolete since Proxmox introduced native support for dark-mode in one of the later 7.3-Versions of PVE and PBS.
see: [link](https://github.com/Weilbyte/PVEDiscordDark)

# docker inside LXC

# install PBS in a Container

# running tailscale in a Container

To bring up Tailscale in an unprivileged container, access to the /dev/tun device can be enabled in the config for the LXC.  For example, using Proxmox 7.0 to host as unprivileged LXC with ID 112, the following lines would be added to /etc/pve/lxc/112.conf:

```sh
lxc.cgroup2.devices.allow: c 10:200 rwm
lxc.mount.entry: /dev/net/tun dev/net/tun none bind,create=file
```

see: https://tailscale.com/kb/1130/lxc-unprivileged/#instructions

### vice-versa non-tailscale-container on an tailscale-proxmox-host

By default Proxmox writes its own DNS config to /etc/resolv.conf within LXCs. Even if the LXC gets its DNS configuration via DHCP, Proxmox will overwrite /etc/resolv.conf with its own. If Tailscale is installed on Proxmox and using MagicDNS, Proxmox will write that config to the container’s /etc/resolv.conf:

```sh
# --- BEGIN PVE ---
nameserver 100.100.100.100
search example.ts.net
# --- END PVE ---
```

If the LXC itself does not have Tailscale installed, this configuration is unlikely to work and DNS lookups will time out.

Two options to mitigate this behavior are:

- Configure tailscale without MagicDNS on the Proxmox host with `tailscale up --accept-dns=false`.
- Create a file named `/etc/.pve-ignore.resolv.conf` _within each LXC’s filesystem_ that will tell Proxmox not to overwrite /etc/resolv.conf.

see: https://tailscale.com/kb/1133/proxmox/

# use host-storage via mountpoints in containers

see: https://pve.proxmox.com/wiki/Unprivileged_LXC_containers

# shrink size of a root-disk on zfs

1. change quota and refquota to the desired size:
```sh
zfs set quota=32G rpool/data/subvol-<CT-ID>-disk-0
zfs set refquota=32G rpool/data/subvol-<CT-ID>-disk-0
```
2. change size in `/etc/pve/nodes/<NODE-NAME>/lxc/<CT-ID>.conf` to the same value in the rootfs-line. 

Note: for non-zfs filesystems it is more complicated to shrink a root-disk. Increasing the size is reather easy via the gui. 