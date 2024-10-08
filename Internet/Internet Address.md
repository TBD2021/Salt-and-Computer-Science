# Internet Address

**Topics:**

- Internet Address

## Internet Address

每个联入互联网的计算机都需要有一个独一无二的地址。Internet addresses的格式是 nnn.nnn.nnn.nnn ，这里 nnn 必须是一个0~255之间的数字，这个地址就是所谓的IP地址（IP指 “Internet Protocol，互联网协议” ）。

- If you connect to the Internet through an Internet Service Provider (ISP), you are usually assigned a temporary IP address for the duration of your dial-in session.
- If you connect to the Internet from a local area network (LAN) your computer might have a permanent IP address or it might obtain a temporary one from a DHCP (Dynamic Host Configuration Protocol) server. 


<!--
**字符串匹配问题**

假设有一个长度为 n 的字符串 T（称为文本）和一个长度为 m (m ≤ n) 的字符串 P（称为模式串）。如果文本 T 中自第 s+1 个字符到第 s+m 个字符与模式串 P 完全相同，则称为模式串 P 在文本 T 中出现且有效位移为 s。那么字符串匹配问题就可以简单概括为，在给定的文本 T 中找出模式串 P 的所有有效位移 s。

在字符串匹配问题中，用n表示文本 T 的长度，m 表示模式串 P 的长度，用符号 Σ 表示由所有字符构成的字母表，Σ 是一个有限集合。

## 暴力算法

用暴力算法（Brute Force）解决字符串匹配问题，就是从文本 T 的第一个字符开始，从前向后逐个比较，判断是否与模式串 P 匹配。

**时间复杂度**

暴力算法一共要比较 n-(m-1)次，每次比较 m 个字符，因此时间复杂度为 O((n-m+1)*m)。

-->
