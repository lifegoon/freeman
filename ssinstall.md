1. yum install m2crypto python-setuptools
2. easy_install pip
3. pip install shadowsocks
4. vi  /etc/shadowsocks.json
```
{
    "server":"0.0.0.0",
    "server_port":443,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"123456",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```
5. 安装防火墙 启动防火墙
```
yum install firewalld
systemctl start firewalld
```
6. 开启防火墙相应的端口
```
端口号是你自己设置的端口
$ firewall-cmd --permanent --zone=public --add-port=443/tcp
$ firewall-cmd --reload
```
7. 启动 Shadowsocks 服务
```
ssserver -c /etc/shadowsocks.json
or
ssserver -c /etc/shadowsocks.json -d start

ssserver -c /etc/shadowsocks.json -d stop
```
