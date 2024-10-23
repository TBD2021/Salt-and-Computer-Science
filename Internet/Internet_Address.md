# Internet Address, Protocol Stacks and Packets, Networking Infrastructure

**Topics:**

- Internet Address
  - Internet Address
  - the "Ping" Program
- Protocol Stacks and Packets
- Networking Infrastructure

## Internet Address

每个联入互联网的计算机都需要有一个独一无二的地址。Internet addresses的格式是 nnn.nnn.nnn.nnn ，这里 nnn 必须是一个0~255之间的数字，这个地址就是所谓的IP地址（IP指 “Internet Protocol，互联网协议” ）。

- If you connect to the Internet through an Internet Service Provider (ISP), you are usually assigned a temporary IP address for the duration of your dial-in session.
- If you connect to the Internet from a local area network (LAN) your computer might have a permanent IP address or it might obtain a temporary one from a DHCP (Dynamic Host Configuration Protocol) server. 

## the "Ping" Program

The "Ping" program is to see if a computer on the Internet is alive. The ping program will send a 'ping' (actually an ICMP (Internet Control Message Protocol) echo request message) to the named computer. The pinged computer will respond with a reply. The ping program will count the time expired until the reply comes back (if it does). Also, if you enter a domain name (i.e. www.yahoo.com) instead of an IP address, ping will resolve the domain name and display the computer's IP address. More on domain names and address resolution later.

**【例-Windows操作系统下使用Ping程序】**

0. 打开cmd程序。
1. 输入`ping www.yahoo.com`。

## 协议栈和数据包（Protocol Stacks and Packets）

计算机网络上的终端计算机如果想要互相发送信息，是如何将字符内容转换为电信号通过计算机网络传递到目标终端，然后再被解读出来的呢？这个过程是通过协议栈（Protocal Stack）实现的。这个协议栈就是TCP/IP协议（主要由TCP协议、IP协议两个通信协议构成），如下表所示
| Protocol Layer| Comments |
| ----------- | ----------- |
| Application Protocols Layer| Protocols specific to applications such as WWW, e-mail, FTP, etc.       |
| Transmission Control Protocol Layer   | TCP directs packets to a specific application on a computer using a port number.        |
| Internet Protocol Layer   | IP directs packets to a specific computer using an IP address.        |
| Hardware Layer   | Converts binary packet data to network signals and back.(E.g. ethernet network card, modem for phone lines, etc.)  |

If we were to follow the path that the message "Hello computer 5.6.7.8!" took from our computer(IP address is 1.2.3.4) to the computer with IP address 5.6.7.8, it would happen something like this:

<div align="center">
<img src="https://github.com/TBD2021/Salt-and-Computer-Science/blob/main/Internet/img/TCPIPLayer.png" width=380px>
</div>

1. The message would start at the top of the protocol stack on your computer and work it's way downward.
2. If the message to be sent is long, each stack layer that the message passes through may break the message up into smaller chunks of data. This is because data sent over the Internet (and most computer networks) are sent in manageable chunks. On the Internet, these chunks of data are known as packets.
3. The packets would go through the Application Layer and continue to the TCP layer. Each packet is assigned a port number. Ports will be explained later, but suffice to say that many programs may be using the TCP/IP stack and sending messages. We need to know which program on the destination computer needs to receive the message because it will be listening on a specific port.
4. After going through the TCP layer, the packets proceed to the IP layer. This is where each packet receives it's destination address, 5.6.7.8.
5. Now that our message packets have a port number and an IP address, they are ready to be sent over the Internet. The hardware layer takes care of turning our packets containing the alphabetic text of our message into electronic signals and transmitting them over the phone line.
On the other end of the phone line your ISP has a direct connection to the Internet. The ISPs router examines the destination address in each packet and determines where to send it. Often, the packet's next stop is another router. More on routers and Internet infrastructure later.
Eventually, the packets reach computer 5.6.7.8. Here, the packets start at the bottom of the destination computer's TCP/IP stack and work upwards.
6. As the packets go upwards through the stack, all routing data that the sending computer's stack added (such as IP address and port number) is stripped from the packets.
7. When the data reaches the top of the stack, the packets have been re-assembled into their original form, "Hello computer 5.6.7.8!"








