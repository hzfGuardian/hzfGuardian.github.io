
##给树莓派换个linux内核

在ubuntu-16.04上面玩了一发树莓派的内核交叉编译，然后发现人民怨声载道啊尤其那个不忍直视的树莓派内核源码github链接的下载速度简直了啊啊啊。为了不在板子上跑出12个小时的编译内核过程，还是上车搞个交叉编译好了。

<html>
[<p style="text-align:right"> Read More... <p>](posts/rpikernel.html)
</html>

---

## 如何在七块钱的板子上重写`delay_ms`和`delay_us`

所谓的七块钱的板子啊，不用说也知道说的是谁。多说无益进去上车再说……

<html>
[<p style="text-align:right"> Read More... <p>](posts/stm32delayus.html)
</html>

---

## Mac OS上配置Raspberry Pi的ARM交叉编译环境

1. 下载编译工具链 ARMx-2009q3-67.tar.bz2

2. 新建一个磁盘映像: 打开 Disk Utility -> File -> New Image -> Blank Image...

<html>
[<p style="text-align:right"> Read More... <p>](posts/ARM_Cross.html)
</html>

---

## Use Xmodem On Mac OS X

在没有路由的情况下，要连接嵌入式板卡传输文件，需要串口通信。本文介绍的就是用Xmodem在Mac和树莓派之间进行串口通信的实例...

<html>
[<p style="text-align:right"> Read More... <p>](posts/xmodem.html)
</html>

---

## Install Xilinx ISE 14.7 on Windows 10


The problem is, default xilinx barely works in 64-bit mode on Windows 8 :palm: The license manager and Project Navigator both just close when you try to open a file and PlanAhead only works in 32-bit mode. Now we do some extra jobs to make it works. 

<html>
[<p style="text-align:right"> Read More... <p>](posts/Xilinx.html)
</html>

---

## Use OpenMP On Xcode

Sometimes we need to use parallel frameworks on xcode projects(Maybe OpenGL or Unity3D or others), in this blog we introduce how to setup openmp environment on xcode 7.3.1.

[<p style="text-align:right"> Read More... <p>](posts/openmp.html)
