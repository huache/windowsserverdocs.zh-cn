---
title: Hyper-v 上支持的 Oracle Linux 虚拟机
description: 列出每个版本中包含的 Linux integration services 和功能
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: c02fdb5b-62f3-43cb-a190-ab74b3ebcf77
author: shirgall
ms.author: kathydav
ms.date: 06/05/2020
ms.openlocfilehash: 67f38d11c032e9eb0b98da14c25e01a5f67cabae
ms.sourcegitcommit: 76a3b5f66e47e08e8235e2d152185b304d03b68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663170"
---
# <a name="supported-oracle-linux-virtual-machines-on-hyper-v"></a>Hyper-v 上支持的 Oracle Linux 虚拟机

>适用于： Windows Server 2019，Windows Server 2016，Hyper-v Server 2016，Windows Server 2012 R2，Hyper-v Server 2012 R2，Windows 10，Windows 8。1

以下功能分发映射指示每个版本中的功能。 表后面列出了每个分发的已知问题和解决方法。

本部分内容：

* [Oracle Linux 3.x 系列](#oracle-linux-8x-series)
* [Oracle Linux 7. x 系列](#oracle-linux-7x-series)
* [Oracle Linux 1.x 系列](#oracle-linux-6x-series)
 
   
## <a name="table-legend"></a>表图例

* **内置**的-.lis 作为此 Linux 分发的一部分包含在内。 内置 .LIS 的内核模块版本号（如**lsmod**所示）不同于 Microsoft 提供的 .lis 下载包中的版本号。 不匹配并不表明内置的 .LIS 版本已过期。

* &#10004; 功能可用
* （*空白*）-功能不可用
* **RHCK** -Red Hat 兼容内核
* **UEK** -Unbreakable Enterprise KERNEL （UEK） 
   * UEK4-在上游 Linux 内核 release 4.1.12 上构建
   * UEK5-在上游 Linux 内核版本4.14 上构建
   * UEK6-在上游 Linux 内核版本5.4 上构建

## <a name="oracle-linux-8x-series"></a>Oracle Linux 3.x 系列

|       **功能**     |       **Windows Server 版本**      |       **8.0-8.1 （RHCK）** |
|-----------------------|---------------------------------------|-------------------|
|       **可用性**        |   |
|       **[核心](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#core)**      | 2019、2016、2012 R2 | &#10004; | 
|       Windows Server 2016 准确时间       | 2019、2016 | &#10004; | 
|       **[网络](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#networking)**      |   | 
|       Jumbo 帧        | 2019、2016、2012 R2 | &#10004; | 
|       VLAN 标记和中继       | 2019、2016、2012 R2 | &#10004;  | 
|       实时迁移      | 2019、2016、2012 R2 | &#10004; |
|       静态 IP 注入     |  2019、2016、2012 R2 | &#10004; 备注2 | 
|       vRSS     | 2019、2016、2012 R2 | &#10004; |
|       TCP 分段和校验和卸载 | 2019、2016、2012 R2 | &#10004;|
|       SR-IOV  | 2019、2016 |  &#10004;   |
|       **[存储](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#storage)** |  | 
|       VHDX 调整大小  | 2019、2016、2012 R2 | &#10004; |
|       虚拟光纤通道 | 2019、2016、2012 R2 | &#10004; 备注3  |
|       实时虚拟机备份  | 2019、2016、2012 R2 | &#10004; 备注5 |
|       剪裁支持 | 2019、2016、2012 R2 | &#10004;  |
|       SCSI WWN | 2019、2016、2012 R2 | &#10004;  |
|       **[内存](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#memory)** | |
|       PAE 内核支持  | 2019、2016、2012 R2 |  空值 |
|       MMIO 间隙的配置  | 2019、2016、2012 R2 | &#10004; | 
|       动态内存-热添加 | 2019、2016、2012 R2  | &#10004; 注释7、8、9 |
|       动态内存-膨胀 | 2019、2016、2012 R2 | &#10004; 注释7、8、9 |
|       运行时内存大小调整 | 2019、2016  | &#10004;  |
|       **[视频](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#video)** | |
|       Hyper-v 特定视频设备 | 2019、2016、2012 R2 | &#10004;   | 
|       **[其他](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#miscellaneous)** | |
|       键值对  | 2019、2016、2012 R2 | &#10004;   | 
|       不可屏蔽中断 | 2019、2016、2012 R2 | &#10004;  | 
|       从主机到来宾的文件复制 | 2019、2016、2012 R2 | &#10004;  | 
|       lsvmbus 命令 | 2019、2016、2012 R2 | &#10004;  | 
|       Hyper-v 套接字 | 2019、2016 | &#10004;  | 
|       PCI 传递/DDA | 2019、2016 | &#10004; | 
| **[第 2 代虚拟机](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#generation-2-virtual-machines)** | |  |
|       使用 UEFI 启动 | 2019、2016、2012 R2 |  &#10004; 说明12  |   
|       安全启动 | 2019、2016 |  &#10004; | 

## <a name="oracle-linux-7x-series"></a>Oracle Linux 7. x 系列

此系列只有64位内核。

<table width="100%">
<tr height="50px">
<td width="20%" rowspan="2">

Feature
</td>
<td width="20%" rowspan="2">

Windows Server 版本
</td>
<td width="30%" colspan="3">

7.5-7。8
</td>
<td width="30%" colspan="3">

7.3-7。4
</td>
</tr>
<tr>
<td width="20%" colspan="2">

RHCK
</td>
<td width="10%">

UEK5
</td>
<td width="20%" colspan="2">

RHCK
</td>
<td width="10%">

UEK4
</td>
</tr>
<tr>
<td width="20%">

可用性
</td>
<td width="20%">


</td>
<td width="10%">

.LIS 4。3
</td>
<td width="10%">

内置
</td>
<td width="10%">

内置
</td>
<td width="10%">

.LIS 4。3
</td>
<td width="10%">

内置
</td>
<td width="10%">

内置
</td>
</tr>
<tr height="50px">
<td width="20%">

**[核心](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#core)**
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

Windows Server 2016 准确时间
</td>
<td width="20%">

2019、2016
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

 **[网络](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#networking)** 
</td>
<td width="20%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

Jumbo 帧
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">
VLAN 标记和中继
</td>
<td width="20%">
2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

实时迁移
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

静态 IP 注入
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 备注2
</td>
<td width="10%">

&#10004; 备注2
</td>
<td width="10%">

&#10004; 备注2
</td>
<td width="10%">

&#10004; 备注2
</td>
<td width="10%">

&#10004; 备注2
</td>
<td width="10%">

&#10004; 备注2
</td>
</tr>
<tr height="50px">
<td width="20%">

vRSS
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

TCP 分段和校验和卸载
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

SR-IOV
</td>
<td width="20%">

2019、2016
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

**[存储](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#storage)**
</td>
<td width="20%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

VHDX 调整大小
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

虚拟光纤通道
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 备注3
</td>
<td width="10%">

&#10004; 备注3
</td>
<td width="10%">

&#10004; 备注3
</td>
<td width="10%">

&#10004; 备注3
</td>
<td width="10%">

&#10004; 备注3
</td>
<td width="10%">

&#10004; 备注3
</td>
</tr>
<tr height="50px">
<td width="20%">

实时虚拟机备份
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 备注5
</td>
<td width="10%">

&#10004; 注释4，5
</td>
<td width="10%">

&#10004; 备注5
</td>
<td width="10%">

&#10004; 备注5
</td>
<td width="10%">

&#10004; 注释4，5
</td>
<td width="10%">

&#10004; 备注5
</td>
</tr>
<tr height="50px">
<td width="20%">

剪裁支持
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

SCSI WWN
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

**[内存](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#memory)**
</td>
<td width="20%">


</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

PAE 内核支持
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

空值
</td>
<td width="10%">

空值
</td>
<td width="10%">

空值
</td>
<td width="10%">

空值
</td>
<td width="10%">

空值
</td>
<td width="10%">

空值
</td>
</tr>
<tr height="50px">
<td width="20%">

MMIO 间隙的配置
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

动态内存热添加
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 注释7、8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
</tr>
<tr height="50px">
<td width="20%">

动态内存膨胀
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 注释7、8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
<td width="10%">

&#10004; 注释8、9
</td>
</tr>
<tr height="50px">
<td width="20%">

运行时内存大小调整
</td>
<td width="20%">

2019、2016
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

**[视频](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#video)**
</td>
<td width="20%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

Hyper-v 特定视频
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

**[其他](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#miscellaneous)**
</td>
<td width="20%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

键值对
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

不可屏蔽中断
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

从主机到来宾的文件复制
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

lsvmbus 命令
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

Hyper-v 套接字
</td>
<td width="20%">

2019、2016
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">


</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

PCI 传递/DDA
</td>
<td width="20%">

2019、2016
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
<tr height="50px">
<td width="20%">

**[第 2 代虚拟机](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#generation-2-virtual-machines)**
</td>
<td width="20%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
<td width="10%">

</td>
</tr>
<tr height="50px">
<td width="20%">

使用 UEFI 启动
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004; 说明12
</td>
<td width="10%">

&#10004; 说明12
</td>
<td width="10%">

&#10004; 说明12
</td>
<td width="10%">

&#10004; 说明12
</td>
<td width="10%">

&#10004; 说明12
</td>
<td width="10%">

&#10004; 说明12
</td>
</tr>
<tr height="50px">
<td width="20%">

安全启动
</td>
<td width="20%">

2019、2016、2012 R2
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
<td width="10%">

&#10004;
</td>
</tr>
</table>


## <a name="oracle-linux-6x-series"></a>Oracle Linux 1.x 系列

此系列只有64位内核。

|       **功能**     |       **Windows Server 版本**      |       **6.8-6.10 （RHCK）** |       **6.8-6.10 （UEK4）**     | 
|-----------------------|---------------------------------------|-------------------|-------------------|
|       **可用性**     |   | .LIS 4。3  | 内置  |
|       **[核心](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#core)**      | 2019、2016、2012 R2 | &#10004; | &#10004;
|       Windows Server 2016 准确时间       | 2019、2016 | | 
|       **[网络](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#networking)**      |   |  |
|       Jumbo 帧        | 2019、2016、2012 R2 | &#10004; | &#10004;|
|       VLAN 标记和中继       | 2019、2016、2012 R2 | &#10004; 注释1 | &#10004; 注释1 |
|       实时迁移      | 2019、2016、2012 R2 | &#10004; | &#10004;|
|       静态 IP 注入     |  2019、2016、2012 R2 | &#10004; 备注2 | &#10004;|
|       vRSS     | 2019、2016、2012 R2 | &#10004; | &#10004;|
|       TCP 分段和校验和卸载 | 2019、2016、2012 R2 | &#10004;|  &#10004; |
|       SR-IOV  | 2019、2016 |    |  |
|       **[存储](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#storage)** |  |  |
|       VHDX 调整大小  | 2019、2016、2012 R2 | &#10004; | &#10004; |
|       虚拟光纤通道 | 2019、2016、2012 R2 | &#10004; 备注3  | &#10004; 备注3 |
|       实时虚拟机备份  | 2019、2016、2012 R2 | &#10004; 备注5 | &#10004; 备注5|
|       剪裁支持 | 2019、2016、2012 R2 | &#10004;  | &#10004; |
|       SCSI WWN | 2019、2016、2012 R2 | &#10004;  | &#10004; |
|       **[内存](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#memory)** | |  |
|       PAE 内核支持  | 2019、2016、2012 R2 |  空值 | 空值
|       MMIO 间隙的配置  | 2019、2016、2012 R2 | &#10004; | &#10004;  |
|       动态内存-热添加 | 2019、2016、2012 R2  | &#10004; 备注6、8、9 | &#10004; 备注6、8、9 |
|       动态内存-膨胀 | 2019、2016、2012 R2 | &#10004; 备注6、8、9 | &#10004; 备注6、8、9 |
|       运行时内存大小调整 | 2019、2016  |  | |
|       **[视频](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#video)** | | |
|       Hyper-v 特定视频设备 | 2019、2016、2012 R2 | &#10004;   | &#10004; |
|       **[其他](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#miscellaneous)** | | |
|       键值对  | 2019、2016、2012 R2 | &#10004; 说明10，11   | &#10004; 说明10，11  |
|       不可屏蔽中断 | 2019、2016、2012 R2 | &#10004;  | &#10004; |
|       从主机到来宾的文件复制 | 2019、2016、2012 R2 | &#10004;  | &#10004; |
|       lsvmbus 命令 | 2019、2016、2012 R2 | &#10004;  | &#10004; |
|       Hyper-v 套接字 | 2019、2016 | &#10004;  | &#10004; |
|       PCI 传递/DDA | 2019、2016 | &#10004; | &#10004; |
| **[第 2 代虚拟机](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md#generation-2-virtual-machines)** | |  |
|       使用 UEFI 启动 | 2019、2016、2012 R2 |  &#10004; 说明12  | &#10004; 说明12   
|       安全启动 | 2019、2016 |  |  |



## <a name="notes"></a><a name="BKMK_notes"></a>说明

1. 对于此 Oracle Linux 版本，VLAN 标记有效，但 VLAN 中继不起作用。

2. 如果为虚拟机上的指定合成网络适配器配置了网络管理器，则静态 IP 注入可能不起作用。 要使静态 IP 注入正常运行，请确保已完全关闭网络管理器，或已通过 ifcfg-eth0-ethX 文件为特定网络适配器关闭网络管理器。

3.  使用虚拟光纤通道设备时，在 Windows Server 2012 R2 上，请确保已填充逻辑单元号0（LUN 0）。 如果尚未填充 LUN 0，Linux 虚拟机可能无法以本机方式装载光纤通道设备。

4. 对于内置的 .LIS，必须安装 "hyperv-守护程序" 包才能实现此功能。

5.  如果在执行实时虚拟机备份操作的过程中有打开的文件句柄，则在某些角落情况下，备份的 Vhd 可能需要在还原时执行文件系统一致性检查（fsck）。 如果虚拟机有连接的 iSCSI 设备或直接连接的存储（也称为传递磁盘），则实时备份操作可能会悄悄地失败。

6. 动态内存支持仅适用于64位虚拟机。

7. 默认情况下，此分发中未启用热添加支持。 若要启用热添加支持，需要在/etc/udev/rules.d/下添加 udev 规则，如下所示：

   1. 创建文件 **/etc/udev/rules.d/100-balloon.rules**。 您可以为该文件使用任何其他所需的名称。

   2. 将以下内容添加到文件：`SUBSYSTEM=="memory", ACTION=="add", ATTR{state}="online"`

   3. 重新启动系统以启用热添加支持。

   尽管 Linux Integration Services 下载会在安装时创建此规则，但卸载 .LIS 时也会删除该规则，因此，如果在卸载之后需要动态内存，则必须重新创建该规则。

8. 如果来宾操作系统在内存上运行得太低，动态内存操作可能会失败。 下面是一些最佳做法：

   * 启动内存和最小内存应等于或大于分发供应商建议的内存量。

   * 通常会消耗系统中的全部可用内存的应用程序，仅消耗最多80% 的可用 RAM。

9. 如果在 Windows Server 2016 或 Windows Server 2012 R2 操作系统上使用动态内存，请以128兆字节（MB）为单位指定 "**启动内存**"、"**最小内存**" 和 "**最大内存**" 参数。 如果不这样做，可能会导致热添加失败，并且在来宾操作系统中可能看不到任何内存增长。

10. 若要启用键/值对（KVP）基础结构，请从 Oracle Linux ISO 安装 hypervkvpd 或 hyperv-守护程序 rpm 包。 或者，可以直接从 Oracle Linux Yum 存储库安装包。

11. 如果没有 Linux 软件更新，键/值对（KVP）基础结构可能无法正常运行。 请与您的分销商联系以获取软件更新，以防您看到此功能的问题。

12. 在 Windows Server 2012 R2 第2代虚拟机上，默认情况下已启用安全启动，某些 Linux 虚拟机将无法启动，除非禁用了安全启动选项。 你可以在**Hyper-v 管理器**中虚拟机设置的 "**固件**" 部分禁用安全启动，也可以使用 Powershell 禁用它：

    ```Powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```

    可以将 Linux Integration Services 下载应用到现有的第2代 Vm，但不授予第2代功能。


另请参阅

* [Set-vmfirmware](https://technet.microsoft.com/library/dn464287.aspx)

* [Hyper-v 上支持的 CentOS 和 Red Hat Enterprise Linux 虚拟机](Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md)

* [Hyper-V 上支持的 Debian 虚拟机](Supported-Debian-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 SUSE 虚拟机](Supported-SUSE-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 Ubuntu 虚拟机](Supported-Ubuntu-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上支持的 FreeBSD 虚拟机](Supported-FreeBSD-virtual-machines-on-Hyper-V.md)

* [Hyper-v 上的 Linux 和 FreeBSD 虚拟机的功能说明](Feature-Descriptions-for-Linux-and-FreeBSD-virtual-machines-on-Hyper-V.md)

* [在 Hyper-v 上运行 Linux 的最佳实践](Best-Practices-for-running-Linux-on-Hyper-V.md)
