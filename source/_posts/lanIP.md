---
title: lanIP
date: 2023-03-13 12:56:32
tags:  ["ip","bug","局域网","DHCP","路由器","路由表"]
---
# 路由寻址的摸索
个人理解，ip对应网卡，实际是多个虚拟网卡。mac对应主机，实际是对应端口号。
自己下午测了一下路由的各种情况，画了个表，大概知道路由器会有路由表，寻址时先广播找MAC。
<!-- more -->
<img src=2023_3_lanip01.png width="100%" alt="测试图片" >
4.在同一个wifi下（应该是同频率下），192.168.8.5（包装自己的Mac）在广播寻址192.168.8.2，在相同频段内连接的所有的网卡均能收到8.5寻找8.2信息，只要自身是8.2就可以回复并发送自己的Mac，不是8.2的不回复（存在多个冲突，推测先到先得），8.5在根据目标8.2的mac发送报文。（本次的路由器ip为192.169.0.1/24，与子网不同，推测路由器并不会在路由表中维护8.5的ipmac关系或者说路由器根本收不到广播？如果路由器ip192.168.8.1/24等包含8.5ip，则会维护）。


