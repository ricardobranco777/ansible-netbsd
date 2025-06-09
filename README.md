# ansible-netbsd

Ansible configuration for NetBSD 10.x

Run as root:

```
PKG_PATH="https://cdn.NetBSD.org/pub/pkgsrc/packages/NetBSD/$(uname -p)/$(uname -r | cut -d_ -f1)/All"
export PKG_PATH
pkg_add -v pkgin
pkgin update
pkgin install python313
echo PermitRootLogin prohibit-password >> /etc/ssh/sshd_config
service sshd restart
pkg_admin -K /usr/pkg/pkgdb fetch-pkg-vulnerabilities
pkg_admin audit
```

Check:
`ansible-playbook -v -C -i inventory.yml main.yml`

Run with:
`ansible-playbook -v -i inventory.yml main.yml`

To remount `/` read-write in single user mode:
`mount -u /`
