### ssh
其实ssh很容易理解，通过命令行可以生成2把钥匙：一把公钥，一把私钥。公钥需要安装在服务器端

### Safe guarantee
改变默认端口并拒绝root登录,配置iptables和Fail2Ban增强安全防护
- [改变默认端口并拒绝root登录](https://github.com/ScottXiong/ssh/blob/master/files/node_prot.md)
- [配置iptables](https://github.com/ScottXiong/ssh/blob/master/files/iptables.md)
- [配置Fail2Ban](https://github.com/ScottXiong/ssh/blob/master/files/fail2ban.md)
### 安全评估
经过一些列的安全防护，vps的安全等级得以提升，比起大型的安全防护虽显得弱小，但是对付一些日常的攻击已绰绰有余。
当然如果要深入安全防护，就要多学学运维的知识了
