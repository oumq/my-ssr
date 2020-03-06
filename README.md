# my-ssr
科学上网，ssr走一波

## 服务器
    目前白嫖谷歌云嘻嘻嘻
## 初始化脚本
* Ubuntu/Debian
````
apt-get update
apt-get install git python-m2crypto libsodium18
cd /usr/local
git clone -b manyuser https://github.com/shadowsocksrr/shadowsocksr.git
cd shadowsocksr
bash initcfg.sh
````
* CentOS
````
yum update
yum install git python-m2crypto libsodium18
cd /usr/local
git clone -b manyuser https://github.com/shadowsocksrr/shadowsocksr.git
cd shadowsocksr
bash initcfg.sh
````
## 更改配置文件信息
````
cd /usr/local/shadowsocksr
vi user-config.json
````
    主要修改端口号及密码，加密、协议、混淆可根据自己需求求改
    加密：
    none	aes-256-gcm	aes-192-gcm	aes-128-gcm
    aes-256-cfb	aes-192-cfb	aes-128-cfb	aes-256-cfb8
    aes-192-cfb8	aes-128-cfb8	aes-256-ctr	aes-192-ctr
    aes-128-ctr	chacha20-ietf	chacha20	rc4-md5
    rc4-md5-6
    
    协议：
    origin	verify_deflate	auth_sha1_v4	auth_sha1_v4_compatible
    auth_aes128_md5	auth_aes128_sha1	auth_chain_a	auth_chain_b
    
    混淆：
    plain	http_simple	http_simple_compatible
    http_post	http_post_compatible	tls1.2_ticket_auth
    tls1.2_ticket_auth_compatible	tls1.2_ticket_fastauth	tls1.2_ticket_fastauth_compatible
## 加速
    wget --no-check-certificate https://github.com/Ellean/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
    校验是否成功开启BBR
    命令	                                            一般返回值
    sysctl net.ipv4.tcp_available_congestion_control	net.ipv4.tcp_available_congestion_control = bbr cubic reno
    sysctl net.ipv4.tcp_congestion_control	net.ipv4.tcp_congestion_control = bbr
    sysctl net.core.default_qdisc	net.core.default_qdisc = fq

## 启动
    cd /usr/local/shadowsocksr/shadowsocks
    ./logrun.sh 或者 ./tail.sh
    
## ssr客户端
    https://github.com/shadowsocksrr

## 原文链接
    https://www.wervps.com/we/1142.html
