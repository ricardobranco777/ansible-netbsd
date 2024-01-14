
```
cd /usr/src/sys/arch/amd64/conf/
config CUSTOM
cd /usr/src
./build.sh -j4 -U -u distribution
./build.sh -j4 -U -u kernel=CUSTOM

sudo cp /netbsd /netbsd.old
sudo cp /usr/obj/sys/arch/amd64/compile/CUSTOM/netbsd /
sudo shutdown -r now

cd /usr/src
sudo ./build.sh -U install=/

sudo /usr/sbin/postinstall -s /usr/src check
sudo /usr/sbin/postinstall -s /usr/src fix
sudo /usr/sbin/etcupdate -s /usr/src
```
