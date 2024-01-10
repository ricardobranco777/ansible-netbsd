# ansible-netbsd

Ansible configuration for NetBSD 10

Run:

```
PKG_PATH="https://cdn.NetBSD.org/pub/pkgsrc/packages/NetBSD/$(uname -p)/$(uname -r | cut -d_ -f1)/All"
export PKG_PATH
pkg_add -v pkgin
pkgin update
pkgin install python311
echo PermitRootLogin prohibit-password >> /etc/ssh/sshd_config
service sshd restart
```

Check:
`ansible-playbook -v -C -i inventory main.yml`

Run with:
`ansible-playbook -v -i inventory main.yml`

TODO:
- Configure /etc/nsswitch.conf for multicast_dns
- NPF
