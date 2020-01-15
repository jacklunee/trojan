#
首先要感谢atrandys大神提供的一键安装脚本！
# 
最简单的Trojan一键脚本，效率高/速度快/延迟低，支持tls1.3，系统支持centos7+/debian9+/ubuntu16+
#
使用方法
1、执行以下脚本，然后选择1，安装trojan，然后输入解析到VPS的域名，回车安装即可。注意：安装时不要开启CDN，否则会提示IP地址不匹配。
#
curl -O https://raw.githubusercontent.com/jacklunee/trojan/master/trojan_mult.sh && chmod +x trojan_mult.sh && ./trojan_mult.sh
#
2、下载客户端、安装浏览器插件，启用trojan

这里的教程其实很简单，脚本安装完成会提示一个下载地址，复制到浏览器即可下载windows版客户端，然后需要配合浏览器插件使用。

#
关于申请证书没有成果的处理

出现这个问题最可能的原因之一是你的同一个域名多次申请证书，导致let’s encrypt官方的限制，同一域名每周最多5次申请。


如果你的同一个域名申请了很多此证书，这个处理方法可能有用：更换二级域名，例如原来使用的域名是www.abc.com或abc.com或xyz.abc.com，那么现在你添加一个二级域名解析例如xxx.abc.com，安装时使用这个域名即可。
#
电脑上其他软件如何使用Trojan
1、如果软件支持配置socks5，直接指向127.0.0.1：1080即可。

2、如果软件不支持配置socks5，可选择sstap/sockscap64/supercap等软件，曲线实现代理。

3、trojan服务端怎么修改密码

trojan服务端配置文件路径如下，如需修改内容，修改以下文件即可。
#
/usr/src/trojan/server.conf
#
修改完成后，重启trojan服务端即可，同时客户端的密码也要同步修改哦。
#
重启代码 systemctl restart trojan
#
安装完成后，会展示一条下载地址，复制地址，并下载下来即可。

如果你真的忘记下载了，那么进入/usr/share/nginx/html/目录下，找到一个乱码文件夹，进入会看到客户端文件，使用sftp下载下来即可。
#
DO主机如果出现登录后不能显示页面解决办法
1、用代理应急
2、修改hosts文件
——————————————————————————————————————————————————————
DO用的ccs的CDN中转服务是fastly公司的，解析时会被墙！用ping工具找出IP地址
hosts里面加入 151.101.1.194  cloud-cdn-digitalocean-com.global.ssl.fastly.net
——————————————————————————————————————————————————————
怎么找出网站被墙的部分？
1、用chrome浏览器右键——检查——console找出加载失败的CSS和JS等等
2、ping出该网址被墙的真实IP（选择海外的），如果IP能ping得通，证明IP可用修改hosts文件即可
#
自动配置伪装网站，位于/usr/share/nginx/html/目录下，可自行替换其中内容

