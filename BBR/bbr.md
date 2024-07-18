
## Debian Base:

### Tcp-Tweaker 

```
bash <(curl -Ls https://raw.githubusercontent.com/xpanel-cp/XPanel-SSH-User-Management/master/TCP-Tweaker --ipv4)
```

### BBR (Normal google BBR)
```
wget --no-check-certificate -O /opt/bbr.sh https://github.com/teddysun/across/raw/master/bbr.sh && chmod 755 /opt/bbr.sh && bash /opt/bbr.sh
```

## CentOS

### BBR plus
```
wget "https://github.com/cx9208/bbrplus/raw/master/ok_bbrplus_centos.sh" && chmod +x ok_bbrplus_centos.sh && ./ok_bbrplus_centos.sh
```

### BBR (Normal google BBR)
```
wget --no-check-certificate -O /opt/bbr.sh https://github.com/teddysun/across/raw/master/bbr.sh && chmod 755 /opt/bbr.sh && bash /opt/bbr.sh
```

## OpenVZ
```
wget --no-check-certificate https://raw.githubusercontent.com/cloudstarry/google-bbr/master/bbrvz.sh && bash bbrvz.sh
```

ping 10.0.0.2 // if it returns delay, done

Change Speed up Port Range:(search 9000-9999)

```
nano /root/lkl/run.sh
```
```
nano /root/lkl/haproxy.cfg
```
