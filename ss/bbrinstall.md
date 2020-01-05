## Method1 Oneshot install
root
```
$ wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```
### check core
```
$ uname -r
```
### check tcp control
```
$ sysctl net.ipv4.tcp_available_congestion_control

net.ipv4.tcp_available_congestion_control = reno cubic bbr

$ sysctl net.ipv4.tcp_congestion_control
net.ipv4.tcp_congestion_control = bbr

$ sysctl net.core.default_qdisc
net.core.default_qdisc = fq

$ lsmod | grep bbr
tcp_bbr                20480  11
```

## Method2 manual install 
## Requirements for Linux server Internet speed with TCP BBR
Make sure that your Linux kernel has the following option compiled as either module or inbuilt
into the Linux kernel:
1. CONFIG_TCP_CONG_BBR
2. CONFIG_NET_SCH_FQ

### Part 1 About System Core
BBR need Linux kernel version 4.9 or above
1. check option
```
uname -r
grep 'CONFIG_TCP_CONG_BBR' /boot/config-$(uname -r)
grep 'CONFIG_NET_SCH_FQ' /boot/config-$(uname -r)
egrep 'CONFIG_TCP_CONG_BBR|CONFIG_NET_SCH_FQ' /boot/config-$(uname -r)
```
2. update core
```
rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm
```
3. install core
```
yum --enablerepo=elrepo-kernel install kernel-ml -y
```
4. use core
```
grub2-set-default 1
```
5. reboot system
```
shutdown -r now
```
6. check core version again
```
uname -r
```

### Part 2 Install GOOGLE BBR
1. install
```
echo 'net.core.default_qdisc=fq' | sudo tee -a /etc/sysctl.conf

echo 'net.ipv4.tcp_congestion_control=bbr' | sudo tee -a /etc/sysctl.conf

sysctl -p
```
2. check
```
$ sysctl net.ipv4.tcp_available_congestion_control
net.ipv4.tcp_available_congestion_control = reno cubic bbr

$ sysctl -n net.ipv4.tcp_congestion_control
bbr

$ lsmod | grep bbr
tcp_bbr                20480  8
```
3. tcp_bbr means bbr installed success
