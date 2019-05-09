https://www.vpscn.net/40.html
# 配置文件
config.json
{
    "server": "xyk.azero-ng.cn",
    "server_ipv6": "::",
    "server_port": 443,
    "local_address": "127.0.0.1",
    "local_port": 1080,

    "password": "tutututu",
    "method": "aes-256-cfb",
    "protocol": "origin",
    "protocol_param": "",
    "obfs": "plain",
    "obfs_param": "",
    "speed_limit_per_con": 0,
    "speed_limit_per_user": 0,

    "additional_ports" : {}, // only works under multi-user mode
    "additional_ports_only" : false, // only works under multi-user mode
    "timeout": 120,
    "udp_timeout": 60,
    "dns_ipv6": false,
    "connect_verbose_info": 0,
    "redirect": "",
    "fast_open": false
}

#------------------------------ [ ShadowSocksR ] ------------------------------#
# 安装
修改install_ssr.bash中的文件安装地址。INSTALL_PATH= ‘当前路径’
# 配置
# 启动
bash install_ssr.bash start
# 测试
curl -x socks5://localhost:1080 ip.cn

如果访问不了，使用
bash install_ssr.bash config查看配置是否正确

#-------------------------------- [ Privoxy ] --------------------------------#
# 安装privoxy
sudo pacman -S privoxy
# 配置，/etc/privoxy/config 加入

listen-address  127.0.0.1:1087  # 默认 8118
actionsfile gfwlist.action

# 把gfwlist.action放到privoxy去

sudo cp gfwlist.action /etc/privoxy/

# 启动
sudo systemctl start privoxy.service
bash  install_srr.bash  start
# 测试，
curl -x http://localhost:1087 ip.cn
curl -x http://localhost:1087 www.google.com

#　手动代理设置为启动
http 127.0.0.1 1087
socks 127.0.0.1 1080

# 开机启用
sudo systemctl enable privoxy.service
sudo systemctl start ssr.service
sudo systemctl enable ssr.service

https://github.com/the0demiurge/CharlesScripts/blob/master/charles/bin/ssr
图形界面
https://github.com/erguotou520/electron-ssr/releases

苹果手机SSR客户端：Potatso Lite，Potatso，shadowrocket都可以作为
superwingy，firstwingy，shadowingy，wingy +， banananet，kite-ss proxy，goodshadow，icproyx，shadowrocket等。

 ShadowsocksR账号 配置信息：

 I  P	    : xyk.azero-ng.cn
 端口	    : 443
 密码	    : tutututu
 加密	    : aes-256-cfb
 协议	    : origin
 混淆	    : plain

 Shadowsocks账号 配置信息：
 I  P	    : xyk.azero-ng.cn
 端口	    : 443
 密码	    : tutututu
 加密	    : aes-256-cfb

 SS    链接 :ss://YWVzLTI1Ni1jZmI6dHV0dXR1dHVAeHlrLmF6ZXJvLW5nLmNuOjQ0Mw==
 SSR   链接 :ssr://eHlrLmF6ZXJvLW5nLmNuOjQ0MzpvcmlnaW46YWVzLTI1Ni1jZmI6cGxhaW46ZEhWMGRYUjFkSFUvP29iZnNwYXJhbT0
