### 1. ssh for linux
#### 80 not exists port
```
$ ssh -v -p 80 root@136.244.80.112
OpenSSH_7.9p1, LibreSSL 2.7.3
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug1: Connecting to 136.244.80.112 [136.244.80.112] port 80.
debug1: connect to address 136.244.80.112 port 80: Connection refused
ssh: connect to host 136.244.80.112 port 80: Connection refused
```
#### 8448 invalid port
```
$ ssh -v -p 8448 root@136.244.80.112
OpenSSH_7.9p1, LibreSSL 2.7.3
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug1: Connecting to 136.244.80.112 [136.244.80.112] port 8448.
^C
```
#### 8559 valid port
```
$ ssh -v -p 8559 root@136.244.80.112
OpenSSH_7.9p1, LibreSSL 2.7.3
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug1: Connecting to 136.244.80.112 [136.244.80.112] port 8559.
debug1: Connection established.
debug1: identity file /Users/bryan/.ssh/id_rsa type 0
debug1: identity file /Users/bryan/.ssh/id_rsa-cert type -1
debug1: identity file /Users/bryan/.ssh/id_dsa type -1
debug1: identity file /Users/bryan/.ssh/id_dsa-cert type -1
debug1: identity file /Users/bryan/.ssh/id_ecdsa type -1
debug1: identity file /Users/bryan/.ssh/id_ecdsa-cert type -1
debug1: identity file /Users/bryan/.ssh/id_ed25519 type -1
debug1: identity file /Users/bryan/.ssh/id_ed25519-cert type -1
debug1: identity file /Users/bryan/.ssh/id_xmss type -1
debug1: identity file /Users/bryan/.ssh/id_xmss-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.9
ssh_exchange_identification: Connection closed by remote host
```

### 2. wget for linux
#### 8448 invalid port
```
$ wget 136.244.80.112:8448
--2019-10-29 20:01:09--  http://136.244.80.112:8448/
Connecting to 136.244.80.112:8448... ^C
```
#### 8559 valid port
```
$ wget 136.244.80.112:8559
--2019-10-29 20:05:40--  http://136.244.80.112:8559/
Connecting to 136.244.80.112:8559... connected.
HTTP request sent, awaiting response... No data received.
Retrying.
--2019-10-29 20:05:42--  (try: 2)  http://136.244.80.112:8559/
Connecting to 136.244.80.112:8559... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2019-10-29 20:05:45--  (try: 3)  http://136.244.80.112:8559/
Connecting to 136.244.80.112:8559... ^C
```

### 3. telnet for windows
```
telnet ip port
```
