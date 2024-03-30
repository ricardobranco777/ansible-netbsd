
```
# Make tools
# ./build.sh -j8 -O ../obj -T ../tools -U -u tools

cd /usr/src/sys/arch/amd64/conf/
config CUSTOM
cd /usr/src
./build.sh -j8 -O ../obj -U -u distribution
./build.sh -j8 -O ../obj -U -u kernel=CUSTOM

sudo cp /netbsd /netbsd.old
sudo cp /usr/obj/sys/arch/amd64/compile/CUSTOM/netbsd /
sudo shutdown -r now

cd /usr/src
sudo ./build.sh -O ../obj -T ../tools -U install=/

sudo /usr/sbin/postinstall -s /usr/src check
sudo /usr/sbin/postinstall -s /usr/src fix
sudo /usr/sbin/etcupdate -s /usr/src
```
