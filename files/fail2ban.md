### fail2ban
```
sudo apt-get install fail2ban  //install
y
sudo vi /etc/fail2ban/jail.conf //开始更改配置文件
```
```
只需要更改下列几项
bantime = 600 //默认是600，可以设大一点3600
destemail = root@localhost //换成自己的邮箱
action = %(action_)s //改为%(action_mw)s
```
### 退出
```
sudo service fail2ban status ／／检测fail2ban有没有运行
//fail2ban is running 默认开启
sudo service fail2ban stop //停掉
sudo service fail2ban start／／开启
```
