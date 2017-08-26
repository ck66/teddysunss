Shadowsocks
本脚本适用环境：
系统支持：CentOS，Debian，Ubuntu
内存要求：≥128M
日期：2017 年 07 月 27 日

关于本脚本：
一键安装 ShadowsocksR 服务端。
请下载与之配套的客户端程序来连接。
（以下客户端只有 Windows 客户端和 Python 版客户端可以使用 SSR 新特性，其他原版客户端只能以兼容的方式连接 SSR 服务器）

默认配置：
服务器端口：自己设定（如不设定，默认为 8989）
密码：自己设定（如不设定，默认为 teddysun.com）
加密方式：自己设定（如不设定，默认为 aes-256-cfb）
协议（Protocol）：自己设定（如不设定，默认为 origin）
混淆（obfs）：自己设定（如不设定，默认为 plain）

客户端下载：
Windows / OS X
Linux
Android / iOS
OpenWRT

使用方法：
使用root用户登录，运行以下命令：

wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
安装完成后，脚本提示如下：

Congratulations, ShadowsocksR server install completed!
Your Server IP        :your_server_ip
Your Server Port      :your_server_port
Your Password         :your_password
Your Protocol         :your_protocol
Your obfs             :your_obfs
Your Encryption Method:your_encryption_method

Welcome to visit:https://shadowsocks.be/9.html
Enjoy it!
卸载方法：
使用 root 用户登录，运行以下命令：

./shadowsocksR.sh uninstall
安装完成后即已后台启动 ShadowsocksR ，运行：

/etc/init.d/shadowsocks status
可以查看 ShadowsocksR 进程是否已经启动。
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json
日志文件路径：/var/log/shadowsocks.log
代码安装目录：/usr/local/shadowsocks

多用户配置示例：

{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2"，
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
如果你想修改配置文件，请参考：
https://github.com/breakwa11/shadowsocks-rss/wiki/Server-Setup
https://github.com/breakwa11/shadowsocks-rss/blob/master/ssr.md
https://github.com/breakwa11/shadowsocks-rss/wiki/config.json

更新日志：
2017 年 07 月 27 日：
1、新增：可选协议（protocol）auth_chain_b 。使用该协议需更新到最新版（4.7.0）ShadowsocksR 版客户端；
2、修改：更新 ShadowsocksR 源码下载地址。

2017 年 07 月 22 日：
1、新增：安装时可选 13 种加密方式的其中之一（none 是不加密）。如下所示：

none
aes-256-cfb
aes-192-cfb
aes-128-cfb
aes-256-cfb8
aes-192-cfb8
aes-128-cfb8
aes-256-ctr
aes-192-ctr
aes-128-ctr
chacha20-ietf
chacha20
rc4-md5
rc4-md5-6
2、新增：安装时可选 7 种协议（protocol）的其中之一。如下所示：

origin
verify_deflate
auth_sha1_v4
auth_sha1_v4_compatible
auth_aes128_md5
auth_aes128_sha1
auth_chain_a
auth_chain_b
3、新增：安装时可选 9 种混淆（obfs）的其中之一。如下所示：

plain
http_simple
http_simple_compatible
http_post
http_post_compatible
tls1.2_ticket_auth
tls1.2_ticket_auth_compatible
tls1.2_ticket_fastauth
tls1.2_ticket_fastauth_compatible
2016 年 08 月 13 日：
1、新增多用户配置示例。注意：如果你新增了端口，也要将该端口从防火墙（iptables 或 firewalld）中打开。

2016 年 05 月 12 日：
1、新增在 CentOS 下的防火墙规则设置。

参考链接：
https://github.com/shadowsocksr/shadowsocksr

标签: shadowsocks
