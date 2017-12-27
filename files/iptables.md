# iptables就是防火墙
```
sudo apt-get update && sudu apt-get upgrade  //更新升级ubuntu
iptables -F
提示没有权限
sudo iptables -F  // 清空所有默认规则
sudo vi /etc/iptables.up.rules
```
**配置如下**
```
*filter
# allow all connections
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# allow out traffic
-A OUTPUT -j ACCEPT
# allow http https
-A INPUT -p tcp --ddport 443 -j ACCEPT
-A INPUT -p tcp --dport 80 -j ACCEPT
# allow ssh port login
-A INPUT -p tcp -m state --state NEW --dport 39999 -j ACCEPT  //默认22
# allow ping
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT   
# log denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied:" --log-lever 7
# drop incoming senstive connections
-A INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --set
-A INPUT -p tcp --dport 80 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 150 -j DROP
# reject all other inbound
-A INPUT -j REJECT
-A FORWARD -j REJECT

COMMIT

```

```
编写号配置文件后接下来告诉iptables配置文件在哪里
sudo iptables-restore < /etc/iptables.up.rules
防火墙配置通过后，接下来让防火墙跑起来
sudo ufw status
//Status:inactive,未被激活
sudo ufw enable
y
sudo ufw status
//Status:active
创建shell脚本，开机启动，有时候会遇到停机的情况
sudo vi /etc/network/if-up.d/iptables
```
**配置**
```
#!/bin/sh
iptables-restore /etc/iptables.up.rules
```
**写好配置文件后给权限**
```
sudo chmod +x /etc/network/if-up.d/iptables
```
