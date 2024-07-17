
```
cd /usr/src
./build.sh -j8 -O ../obj -U -u tools
./build.sh -j8 -O ../obj -U -u distribution
./build.sh -j8 -O ../obj -U -u kernel=CUSTOM

# Optional: Make snapshot
sudo fssconfig -c fss0 / /backup

sudo cp -p /netbsd /netbsd.old
sudo cp /usr/obj/sys/arch/$(uname -m)/compile/CUSTOM/netbsd /
sudo shutdown -r now

cd /usr/src
sudo ./build.sh -O ../obj -U install=/

sudo /usr/sbin/postinstall -s /usr/src check
sudo /usr/sbin/postinstall -s /usr/src fix opensslcertsrehash
sudo /usr/sbin/etcupdate -s /usr/src

# Optional: Delete snapshot
sudo fssconfig -x fss0 / /backup
```
