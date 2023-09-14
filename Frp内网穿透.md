# 工具下载
Frp工具下载地址:<a href="https://github.com/fatedier/frp/releases">下载地址</a>

Mac系统下载：darwin_amd64

Linux下载：linux_amd64

windows下载：windows_386
# 公网服务端--有公网ip
```shell
mkdir ~/frp
```
解压工具包，进入目录
```shell
tar -zxvf frp.tar.gz
cd frp_xxxx
```
删除frpc和frpc.ini

修改frps.ini
```shell
vim frps.ini

[common]
bind_port = 10086
vhost_http_port = 10010
```
10086和10010端口都必须开放访问

启动服务端
```shell
./frps -c ./frps.ini 前台启动
nohub ./frps -c ./frps.ini 后台启动
```

# 客户端
下载和解压工具包同服务端，然后将frps和frps.ini删除

修改frpc.ini
```shell
[common]
server_addr = xxx.xxx.xxx.xxx  //公网服务端ip
server_port = 10086  //上面配置的bind_port

[web]
type = http
local_ip = 192.1.1.1 //内网服务器ip
local_port = 8080 //内网服务器端口号
custom_domains = xxx.xxx.xxx.xxx //公网服务器ip或者公网服务器域名
```

启动客户端
```shell
./frpc -c ./frpc.ini 前台启动
nohub ./frpc -c ./frpc.ini 后台启动
```
