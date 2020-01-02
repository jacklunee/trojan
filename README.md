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
