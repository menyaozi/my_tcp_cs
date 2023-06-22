# my_tcp_cs

第一次尝试自己写tcp的简单通讯，比较简单，但是还是收获很多

这对tcp的 `client` 和 `server` 是为了验证三挥手和四挥手

* 第 1 次的包中是三挥手，是因为服务端没有需要发送的消息，受到客户端的 `FIN` 后就直接回复 `FIN/ACK` 包，所以是三挥手

* 第 8 次的包中是四挥手，因为收到 `FIN` 包后，服务端还有消息要回，并且要被客户端接受到能优雅的四挥手，否则就会 `RST` 直接关闭

## client的代码编写

* 关闭连接需要使用 `shutdown` 函数 并使用 `SHUT_WR` 参数确保只关闭写，不关闭读。

## server的代码编写
* 同样需要使用 `shutdown` 函数更好
   
## 使用的抓包软件
`tcpdump`

    tcpdump -i lo tcp and port 8888 -s0 -w ./tcp_closex.pcap

分析软件 `Wireshark` 

* 将上面的 `.pacp` 使用该软件打开即可

待续。。。