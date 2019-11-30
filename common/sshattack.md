### look up secure
```
less /var/log/secure
```

### look up btmp
```
last -n numoflines -f /var/log/btmp
```
### find ip attacks counts
```
last -f /var/log/btmp | awk ‘{ print $3}’ | sort | uniq -c | sort -n
```

### change ssh login port
```
$ vi /etc/ssh/sshd_config
1. Uncomment Port 22
2. Add one line after port 22

e.g.
Port 22
Port yourport
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

3. restart service sshd
$ service sshd restart

4. Test your new port 
$ ssh -p yourport user@host

5. Comment sshd_config Port 22
e.g.
#Port 22
Port yourport

6. Restart service sshd
$ service sshd restart
```
