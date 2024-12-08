# Masterclass on "Introduction to VAPT"

![](https://img.shields.io/badge/Batch-21UCYS-lightgreen) ![](https://img.shields.io/badge/Batch-24PCYS-lightgreen) ![](https://img.shields.io/badge/Batch-23PCYS-lightgreen) ![](https://img.shields.io/badge/-VAPT-blue)<br/>
![](https://img.shields.io/badge/Students-75-gold)  <br/>

### Recon
#### Basic IP Scan
```
ifconfig
ping 192.168.2.1-254 ??
nmap –sn 192.168.2.1/24
```

```
nmap -sn -T4 192.168.56.0/24 -vvv
nmap -Pn -F -sSU -T5 10.1.1.1-254 -vvv
```
-Pn=Online, -F=fast/fewer ports, -sSU = combination of UDP and TCP port scanning
-T=Timing (higher is faster)

##### Nmap stealth scan using SYN
```
nmap -sS $ip -vvv
```

##### Discover active IPs using ARP requests on the network
```
sudo arp-scan ip/24
```

##### Discover who else is on the network
```
sudo netdiscover
```

##### TCP Port Scan
```
nmap -Pn -sS --stats-every 3m --max-retries 1 --maxscan-delay 20 --defeat-rst-ratelimit -T4 -p1-65535 192.168.15.201
```

##### Detailed single host TCP scan
```
nmap -nvv -Pn -sSV -T1 –p1-65535 --versionintensity 9 192.168.15.201
```

##### UDP Port Scan
```
nmap -Pn -sSU -T4 -p1-65535 10.1.1.110
```

##### More Commands
```
0) root@kali:~# ls /usr/share/nmap/scripts
1) root@kali:~# nmap -v -p 21 --script=ftp-anon.nse IP
2) root@kali:~# nmap -p25 -sV --script=smtp-vuln* IP
3) root@kali:~# nmap -sT --script nbstat.nse -p139,445 IP
4) root@kali:~# nmap -p139,445 --script=smb-vuln-* --
script-args=unsafe=1 IP
5) root@kali:~# nmap -p 111 --script=nfs-ls IP
6) root@kali:~# telnet IP / nc IP port
7) nmap -p 80 -sTV -n -sV -sC --script=httpmethods,http-robots.txt,http-vuln-*,httpshellshock,http-userdir-enum,http-iis-webdavvuln,http-majordomo2-dir-traversal,http-axis2-dirtraversal,http-tplink-dir-traversal,http-useragenttester,ssl-* IP
8) nmap -p PORT--script=http-webdav-scan IP
9) nmap -p 80 -sV -sC --script=http-auth-finder,httpbackup-finder,http-comments-displayer,http-configbackup,http-default-accounts,http-dombasedxss,http-errors,http-fileupload-exploiter,httpmethod-tamper,http-passwd,http-phpmyadmin-dirtraversal,http-phpself-xss,http-rfi-spider,httpsitemap-generator,http-sql-injection,http-storedxss,http-unsafe-output-escaping IP
```


