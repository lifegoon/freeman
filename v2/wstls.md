## KVM Centos 7.x
### 魔改加速
```
$ wget --no-check-certificate https://raw.githubusercontent.com/tcp-nanqinlang/general/master/General/CentOS/bash/tcp_nanqinlang-1.3.2.sh
bash tcp_nanqinlang-1.3.2.sh
```

```
1 install core
$ reboot
```

```
press 2 to continue
$ bash tcp_nanqinlang-1.3.2.sh
```
#### 注意：确定域名绑定好IP后，再执行下面的命令

```
curl -O https://raw.githubusercontent.com/atrandys/v2ray-ws-tls/master/v2ray_ws_tls.sh && chmod +x v2ray_ws_tls.sh && ./v2ray_ws_tls.sh
```
> 等待脚本会自动执行，过程中会提示需要输入域名，输入解析到本VPS的域名，然后回车。安装完成后，就你可以看到配置参数。

 ===========配置参数============ 
 地址：cozmo.top 
 端口：443 
 uuid：93008783-5168-49fb-bd12-14d2dfde05aa 
 额外id：64 
 加密方式：aes-128-gcm 
 传输协议：ws 
 别名：myws 
 路径：0190 
 底层传输：tls
