# ssh
其实ssh很容易理解，通过命令行可以生成2把钥匙：一把公钥，一把私钥。公钥需要安装在服务器端
# 改变node服务端访问端口，增加安全防护
默认端口为22，为防止心术不正的人最好改一下磨人端口。那么端口该设为多少呢？默认为0-65536，建议0-1024不要使用，因为很可能被系统占用
```
1，ssh login vps
2. 修改配置
sudo vi ／etc/ssh/sshd_config
提示输入密码
Port 39999
UseDNS no
AllowUsers imooc_manager  ／／新增一行
如果新增用户之后，可以把root登陆关掉，why？因为所有的都叫root，很容易被扫到。为了安全起见，继续修改配置文件
PermitRootLogin no  //默认yes
同时也可以把密码登录关掉
PasswordAuthentication no //不需要授权密码登录，因为已经配置了本地ssh无密码登录
改好之后再检查一下
PermitEmptyPasswords no  //不允许空密码登录的
3.重启服务
sudo service ssh restart ／／每修改一次配置文件都要restart一次
既然修改了端口，那么下次再按老规矩重新登陆必然被refused，因为22端口已不可用
ssh -p 39999 imooc_manager@xx.x.x.x
```
