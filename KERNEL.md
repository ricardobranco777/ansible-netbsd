
```
cd /usr/src
./build.sh -j8 -O ../obj -U -u tools
./build.sh -j8 -O ../obj -U -u distribution
./build.sh -j8 -O ../obj -U -u kernel=CUSTOM

sudo cp /netbsd /netbsd.old
sudo cp /usr/obj/sys/arch/$(uname -m)/compile/CUSTOM/netbsd /
sudo shutdown -r now

cd /usr/src
sudo ./build.sh -O ../obj -U install=/

sudo /usr/sbin/postinstall -s /usr/src check
sudo /usr/sbin/postinstall -s /usr/src fix opensslcertsrehash
sudo /usr/sbin/etcupdate -s /usr/src
```
