### SSH
其实ssh很容易理解，通过命令行可以生成2把钥匙：一把公钥，一把私钥。公钥需要安装在服务器端

### Safe guarantee
改变默认端口并拒绝root登录,配置iptables和Fail2Ban增强安全防护
- [改变默认端口并拒绝root登录](https://github.com/ScottXiong/ssh/blob/master/files/node_prot.md)
- [配置iptables](https://github.com/ScottXiong/ssh/blob/master/files/iptables.md)
- [配置Fail2Ban](https://github.com/ScottXiong/ssh/blob/master/files/fail2ban.md)
### 安全评估
经过一些列的安全防护，vps的安全等级得以提升，虽然这些安全配置很基础，安全等级还不够，但是对付一些日常的恶意攻击已绰绰有余，比一台裸奔的服务器强多了。
当然想要更高的安全等级，就需要更多运维方面的知识储备。比如对生产的服务器的登录设置一个ip的绑定后者限制，只有特定内网ip的机器才能登录到这台服务器。也
就是我们常说的再内网架设一台跳板，通过本地的电脑连上跳板机，再从跳板机登录到生产服务器。
学会了实用服务器，就慢慢打开了新世界的大门，有很多惊喜，也有很多挑战等着我们。
有了这些安全防护，我们就可以把我们的作品放到互联网上。。。
