---
title: prnport
description: 用于创建、删除和列出标准 TCP/IP 打印机端口以及显示和更改端口配置的 prnport 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6a0ec638-a21e-4a34-be5c-bd0f7ca89ffe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4b373547050d3d3dfb1d64160959c8dbb9e6f5c5
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931161"
---
# <a name="prnport"></a>prnport

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

除了显示和更改端口配置之外，还可以创建、删除和列出标准 TCP/IP 打印机端口。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入**cscript** ，然后键入 prnport 文件的完整路径，或将目录更改为相应的文件夹。 例如： `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnport`。

## <a name="syntax"></a>语法

```
cscript prnport {-a | -d | -l | -g | -t | -?} [-r <portname>] [-s <Servername>] [-u <Username>] [-w <password>] [-o {raw | lpr}] [-h <Hostaddress>] [-q <Queuename>] [-n <portnumber>] -m{e | d} [-i <SNMPindex>] [-y <communityname>] -2{e | -d}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| -a | 创建标准 TCP/IP 打印机端口。 |
| -d | 删除标准 TCP/IP 打印机端口。 |
| -l | 列出由 **-s**参数指定的计算机上的所有标准 tcp/ip 打印机端口。 |
| -g | 显示标准 TCP/IP 打印机端口的配置。 |
| -t | 配置标准 TCP/IP 打印机端口的端口设置。 |
| -r`<portname>` | 指定打印机连接到的端口。 |
| -s`<Servername>` | 指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。 |
| -u `<Username>` -w`<password>` | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
| -o`{raw|lpr}` | 指定端口使用的协议： TCP raw 或 TCP lpr。 TCP 原始协议比 lpr 协议在 Windows 上是更高的性能协议。 如果使用 TCP raw，则可以选择使用 **-n**参数指定端口号。 默认端口号为9100。 |
| -h`<Hostaddress>` | 指定要为其配置端口的打印机（按 IP 地址）。 |
| -q`<Queuename>` | 指定 TCP 原始端口的队列名称。 |
| -n`<portnumber>` | 指定 TCP 原始端口的端口号。 默认端口号为9100。 |
| -m`{e|d}` | 指定是否启用 SNMP。 参数**e**启用 SNMP。 参数**d**禁用 SNMP。 |
| -i`<SNMPindex` | 如果启用了 SNMP，则指定 SNMP 索引。 有关详细信息，请参阅[rfc 编辑器网站](https://www.ietf.org/rfc/rfc1759.txt?number=1759)上的**rfc 1759** 。 |
| -y`<communityname>` | 如果启用了 SNMP，则指定 SNMP 共同体名称。 |
| -2`{e|-d}` | 指定是否为 TCP lpr 端口启用双线轴（也称为 respooling）。 双重线轴是必需的，因为 TCP lpr 必须在发送到打印机的控制文件中包含准确的字节计数，但协议无法从本地打印提供程序获取计数。 因此，当文件在后台处理到 TCP lpr 打印队列时，该文件也会在 system32 目录中作为临时文件进行后台处理。 TCP lpr 确定临时文件的大小并将大小发送到运行 LPD 的服务器。 参数**e**启用双重线轴。 参数**d**禁用双重线轴。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来（例如，"计算机名称"）。

### <a name="examples"></a>示例

若要在服务器 Server1 上显示所有标准 TCP/IP 打印端口 \\ ，请键入：

```
cscript prnport -l -s Server1
```

若要删除连接到10.2.3.4 上的网络打印机的服务器 Server1 上的标准 TCP/IP 打印端口 \\ ，请键入：

```
cscript prnport -d -s Server1 -r IP_10.2.3.4
```

若要在10.2.3.4 上添加 \\ 连接到网络打印机并在端口9100上使用 tcp 原始协议的服务器 Server1 上的标准 tcp/ip 打印端口，请键入：

```
cscript prnport -a -s Server1 -r IP_10.2.3.4 -h 10.2.3.4 -o raw -n 9100
```

若要启用 SNMP，请在服务器 Server1 共享的10.2.3.4 上指定 "public" 团体名称并将 "SNMP 索引" 设置为 "1" \\ ，并键入：

```
cscript prnport -t -s Server1 -r IP_10.2.3.4 -me -y public -i 1 -n 9100
```

若要在10.2.3.4 上添加连接到网络打印机的本地计算机上的标准 TCP/IP 打印端口并自动从打印机获取设备设置，请键入：

```
cscript prnport -a -r IP_10.2.3.4 -h 10.2.3.4
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
