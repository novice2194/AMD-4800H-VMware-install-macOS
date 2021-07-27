# 联想拯救者R7000P 2020H黑苹果教程

## 前言

总所周知的原因，macOS支持A卡CPU少之又少，也不支持三星 PM981A的固态，更不支持N卡的GPU。所以我手上的联想拯救者R7000P 2020H就很离谱的满足上述所有条件，即使网上有众多对上述情况魔改的驱动，但同时满足上述情况的驱动根本找不到，即使魔改也是天大的工程。故而只能退而求其次，选择虚拟机运行macOS，又因为大多数基于AMD教程所安装的macOS版本实在古老，且少数新版本的安装教程并不适用，出现各种情况，所以本教程基于联想拯救者R7000P 2020H适配安装较新版本的macOS。



## 硬件：

CPU：AMD 4800H

GPU：NVIDIA RTX 2060

硬盘：三星 PM981A



## 准备工作

虚拟机软件：VMware Workstation Pro 16.X

懒人镜像包：macOS Big Sur 11.4 (20F71).ISO/CDR

VMware Tools镜像文件：darwin.ISO

VMware解锁文件：unlocker-3.0.4

AMD平台代码：

```c
smc.version = "0"
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
cpuid.1.edx = "0000:0111:1000:1011:1111:1011:1111:1111"
smbios.reflectHost = "TRUE"
hw.model = "MacBookPro14,3"
board-id = "Mac-551B86E5744E2388"
keyboard.vusb.enable = "TRUE"
mouse.vusb.enable = "TRUE"
```



## 安装

### 安装系统

0. 以管理员身份运行 win-install.cmd

![image-20210726221327437](%E6%95%99%E7%A8%8B.assets/image-20210726221327437.png)



1. 创建虚拟机

![image-20210726215935404](%E6%95%99%E7%A8%8B.assets/image-20210726215935404.png)



2. 选择典型，下一步

![image-20210726220137937](%E6%95%99%E7%A8%8B.assets/image-20210726220137937.png)



3. 选择ISO文件，下一步

![image-20210726220537410](%E6%95%99%E7%A8%8B.assets/image-20210726220537410.png)



4. 选择Apple Mac OS及版本，下一步

![image-20210726220817417](%E6%95%99%E7%A8%8B.assets/image-20210726220817417.png)



5. 编辑路径，下一步

![image-20210726220909720](%E6%95%99%E7%A8%8B.assets/image-20210726220909720.png)



6. 选择磁盘容量，下一步

![image-20210726221446582](%E6%95%99%E7%A8%8B.assets/image-20210726221446582.png)



7. 自定义硬件（默认即可），完成

![image-20210726221531793](%E6%95%99%E7%A8%8B.assets/image-20210726221531793.png)



8. 打开虚拟机目录（千万别手残开机，开机了会卡第一屏，点了就重新来一遍吧！

![image-20210726221659588](%E6%95%99%E7%A8%8B.assets/image-20210726221659588.png)



9. 打开xxx.vmx文件（用记事本打开就行，记事本yyds）把上面的代码复制粘贴到文本最末尾

![image-20210726222344847](%E6%95%99%E7%A8%8B.assets/image-20210726222344847.png)



10. 开启虚拟机，等上一会

![image-20210726222548701](%E6%95%99%E7%A8%8B.assets/image-20210726222548701.png)



11. 选择简体中文

![image-20210726222756337](%E6%95%99%E7%A8%8B.assets/image-20210726222756337.png)



12. 选择磁盘工具（也别手残点安装，点了不会显示磁盘，安装不了，也退不回来！重启卡第一屏，点了重新再来一遍）

![image-20210726222913890](%E6%95%99%E7%A8%8B.assets/image-20210726222913890.png)



13. 点VMware Virtual SATA Hard

![image-20210726223303304](%E6%95%99%E7%A8%8B.assets/image-20210726223303304.png)



14. 点击抹掉（这里有个细节，如果选择到正确磁盘，此时磁盘大小大概等于第六步设置的大小，且此时显示未初始化）

![image-20210726223543242](%E6%95%99%E7%A8%8B.assets/image-20210726223543242.png)



15. 修改名称，下面两项默认即可（意思是：不要改），然后点击抹掉

![image-20210726223718613](%E6%95%99%E7%A8%8B.assets/image-20210726223718613.png)



16. 完成

![image-20210726223810920](%E6%95%99%E7%A8%8B.assets/image-20210726223810920.png)



17. 点击磁盘工具，退出磁盘工具

![image-20210726223922988](%E6%95%99%E7%A8%8B.assets/image-20210726223922988.png)



18. 点击安装 macOS Big Sur

![image-20210726224110143](%E6%95%99%E7%A8%8B.assets/image-20210726224110143.png)



19. 一路继续、同意

![image-20210726224158599](%E6%95%99%E7%A8%8B.assets/image-20210726224158599.png)

![image-20210726224216150](%E6%95%99%E7%A8%8B.assets/image-20210726224216150.png)

![image-20210726224245497](%E6%95%99%E7%A8%8B.assets/image-20210726224245497.png)



20. 选择磁盘，继续，然后等

![image-20210726224319422](%E6%95%99%E7%A8%8B.assets/image-20210726224319422.png)



等！不要着急

![image-20210726224409498](%E6%95%99%E7%A8%8B.assets/image-20210726224409498.png)

![image-20210726224455918](%E6%95%99%E7%A8%8B.assets/image-20210726224455918.png)

![image-20210726224616248](%E6%95%99%E7%A8%8B.assets/image-20210726224616248.png)

![image-20210726224706992](%E6%95%99%E7%A8%8B.assets/image-20210726224706992.png)



然后会重启一次，以下图为准：

![image-20210726224847861](%E6%95%99%E7%A8%8B.assets/image-20210726224847861.png)



这次重启就很玄学，有的时候可以正常进系统，有的时候不行。

不行的话，进度条卡的位置也不一样，玄学+1，一般在下面这个地方卡掉。

![image-20210726225334506](%E6%95%99%E7%A8%8B.assets/image-20210726225334506.png)



21. 打开任务管理器，查看VMware Workstation VMX进程，如果卡掉了，此处进程磁盘读写应于0.1 MB/秒

![image-20210726225857495](%E6%95%99%E7%A8%8B.assets/image-20210726225857495.png)



磁盘读写为0.1 MB/秒、0MB/秒，直接关闭客户机

![image-20210726231659182](%E6%95%99%E7%A8%8B.assets/image-20210726231659182.png)



打开虚拟机目录，删除上次粘贴结束后新增的的所有代码，并保存：

```c
uma.autosize.cookie = "120122"
numa.autosize.vcpu.maxPerVirtualNode = "8"
uuid.bios = "56 4d dc a8 c6 35 ed 86-7e 9d 4f 41 5b 9d 74 ee"
uuid.location = "56 4d dc a8 c6 35 ed 86-7e 9d 4f 41 5b 9d 74 ee"
sata0:0.redo = ""
pciBridge0.pciSlotNumber = "17"
pciBridge4.pciSlotNumber = "21"
pciBridge5.pciSlotNumber = "22"
pciBridge6.pciSlotNumber = "23"
pciBridge7.pciSlotNumber = "24"
usb.pciSlotNumber = "32"
ethernet0.pciSlotNumber = "160"
sound.pciSlotNumber = "33"
ehci.pciSlotNumber = "34"
usb_xhci.pciSlotNumber = "192"
vmci0.pciSlotNumber = "35"
sata0.pciSlotNumber = "36"
svga.vramSize = "268435456"
vmotion.checkpointFBSize = "134217728"
vmotion.checkpointSVGAPrimarySize = "268435456"
vmotion.svga.mobMaxSize = "268435456"
vmotion.svga.graphicsMemoryKB = "262144"
ethernet0.generatedAddress = "00:0C:29:9D:74:EE"
ethernet0.generatedAddressOffset = "0"
vmci0.id = "1537045742"
monitor.phys_bits_used = "45"
cleanShutdown = "TRUE"
softPowerOff = "FALSE"
usb_xhci:6.speed = "2"
usb_xhci:6.present = "TRUE"
usb_xhci:6.deviceType = "hub"
usb_xhci:6.port = "6"
usb_xhci:6.parent = "-1"
usb_xhci:7.speed = "4"
usb_xhci:7.present = "TRUE"
usb_xhci:7.deviceType = "hub"
usb_xhci:7.port = "7"
usb_xhci:7.parent = "-1"
toolsInstallManager.updateCounter = "11"
usb:1.speed = "2"
usb:1.present = "TRUE"
usb:1.deviceType = "hub"
usb:1.port = "1"
usb:1.parent = "-1"
ethernet0.displayName = "VMnet0"
MemTrimRate = "0"
vhv.enable = "TRUE"
usb.generic.allowHID = "TRUE"
usb_xhci:4.present = "TRUE"
usb_xhci:4.deviceType = "hid"
usb_xhci:4.port = "4"
usb_xhci:4.parent = "-1"
```



22. 重新启动客户机，不出意外，半小时左右，顺利开机

![image-20210726232631769](%E6%95%99%E7%A8%8B.assets/image-20210726232631769.png)

![image-20210726232719425](%E6%95%99%E7%A8%8B.assets/image-20210726232719425.png)





