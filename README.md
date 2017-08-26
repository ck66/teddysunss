![Shadowsocks](https://github.com/teddysun/shadowsocks_install/raw/master/shadowsocks.png)
# Auto install Shadowsocks Server

shadowsocks.sh
===============
- Description: Auto Install Shadowsocks(Python) Server for CentOS/Debian/Ubuntu
- Intro: https://teddysun.com/342.html

shadowsocks-libev.sh
===============
- Description: Auto Install Shadowsocks(libev) Server for CentOS
- Intro: https://teddysun.com/357.html

shadowsocks-libev-debian.sh
===============
- Description: Auto Install Shadowsocks(libev) Server for Debian/Ubuntu
- Intro: https://teddysun.com/358.html

shadowsocks-go.sh
===============
- Description: Auto Install Shadowsocks(Go) Server for CentOS/Debian/Ubuntu
- Intro: https://teddysun.com/392.html

shadowsocks-crond.sh
===============
- Description: Check Shadowsocks(All version) Server is running or not, and start it if not running
- Intro: https://shadowsocks.be/6.html

shadowsocksR.sh
===============
- Description: Auto Install ShadowsocksR Server for CentOS/Debian/Ubuntu
- Intro: https://shadowsocks.be/9.html

shadowsocks-all.sh
==================
- Description: Auto Install Shadowsocks Server (all version) for CentOS/Debian/Ubuntu
- Intro: https://teddysun.com/486.html

haproxy.sh
===============
- Description: Auto Install haproxy for Shadowsocks Server
- Intro: https://shadowsocks.be/10.html

Copyright (C) 2014-2017 Teddysun

# 默认配置：
服务器端口：自己设定（如不设定，默认为 8989）
密码：自己设定（如不设定，默认为 teddysun.com）
加密方式：自己设定（如不设定，默认为 aes-256-cfb）
协议（Protocol）：自己设定（如不设定，默认为 origin）
混淆（obfs）：自己设定（如不设定，默认为 plain）
# 使用方法：
使用root用户登录，运行以下命令：
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh && ./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```
安装完成后，脚本提示如下：
```
Congratulations, ShadowsocksR server install completed!
Your Server IP        :your_server_ip
Your Server Port      :your_server_port
Your Password         :your_password
Your Protocol         :your_protocol
Your obfs             :your_obfs
Your Encryption Method:your_encryption_method

Welcome to visit:https://shadowsocks.be/9.html
Enjoy it!
```
# 卸载方法：
使用 root 用户登录，运行以下命令：
```
./shadowsocksR.sh uninstall
```
安装完成后即已后台启动 ShadowsocksR ，运行：
```
/etc/init.d/shadowsocks status
```
可以查看 ShadowsocksR 进程是否已经启动。
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。
# 使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json
日志文件路径：/var/log/shadowsocks.log
代码安装目录：/usr/local/shadowsocks
# 多用户配置示例：
```
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
```
