# 2024_Project


WG.go
1. https://github.com/WireGuard/wireguard-go

upper layer of obfuscation:
1. https://github.com/wangyu-/udp2raw?tab=readme-ov-file
2. https://github.com/astroza/udptunnel
3. https://github.com/dndx/phantun


已经搭建了wireguard + udp2raw (将UDP流量伪装成TCP流量)，配置如下：
[server]
wireguard 本机IP: 10.8.0.1/24

wireguard 监听端口: 55550
wireguard 接收的IP: 10.8.0.3/24
udp2raw 本地监听: 0.0.0.0:5096
udp2raw 流量转发: 127.0.0.1:55550

[client]
wireguard 本机IP: 10.8.0.3/24
wireguard 接收的IP: 10.8.0.0/24
udp2raw 本地监听: 0.0.0.0:55550
udp2raw 流量转发: 47.100.64.195:5096
指定对端的IP地址和端口号 127.0.0.1:55550


Vultr的服务器在日本：
wg-quick up wg0                    #作为服务器启动
wg-quick up client1                #作为客户端启动
阿里云的服务器在上海：
wg-quick up wg0                    #作为服务器启动
wg-quick up client1                #作为客户端启动
