---
title: 如何在不使用 DHCP 服务器的情况下使用自动 TCP/IP 寻址
description: 介绍如何在没有 DHCP 服务器的情况下使用自动 TCP/IP 寻址。
ms.prod: windows-server
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: troubleshoot
author: Deland-Han
ms.author: delhan
ms.reviewer: robsmi
ms.openlocfilehash: fcd85c29975709053009ec4a2684df88b4bafd69
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409798"
---
# <a name="how-to-use-automatic-tcpip-addressing-without-a-dhcp-server"></a>如何在不使用 DHCP 服务器的情况下使用自动 TCP/IP 寻址

本文介绍如何使用自动传输控制协议/internet 协议（TCP/IP）寻址，而无需在网络中提供动态主机配置协议（DHCP）服务器。 本文 "应用于" 部分中列出的操作系统版本有一项称为自动专用 IP 寻址（APIPA）的功能。 利用此功能，如果 DHCP 服务器不可用或网络上不存在，则 Windows 计算机可以为自身分配 Internet 协议（IP）地址。 此功能使配置和支持运行 TCP/IP 的小型局域网（LAN）变得更加困难。

## <a name="more-information"></a>更多信息

> [!IMPORTANT]
> 请认真遵循本部分所述的步骤。 如果注册表修改不正确，可能会发生严重问题。 在修改注册表之前，请[备份注册表](https://support.microsoft.com/help/322756)，以便在出现问题时可以还原。

如果 DHCP 服务器不可用，则配置为使用 DHCP 的基于 Windows 的计算机可以自动为其分配 Internet 协议（IP）地址。 例如，如果 DHCP 服务器暂时关闭以进行维护，则可能会在没有 DHCP 服务器的网络上或在网络上发生这种情况。

Internet 编号分配机构（IANA）已保留169.254.255.255 用于自动专用 IP 寻址。 因此，APIPA 提供的地址不能与可路由地址冲突。

为网络适配器分配 IP 地址后，计算机可以使用 TCP/IP 与连接到同一 LAN 的任何其他计算机进行通信，也可将其配置为 APIPA，或将 IP 地址手动设置为 169.254. （其中，是客户端的唯一标识符），子网掩码为255.255.0.0。 请注意，计算机无法与其他子网上的计算机或不使用自动专用 IP 寻址的计算机进行通信。 默认情况下启用自动专用 IP 寻址。

在以下任一情况下，你可能想要将其禁用：

- 网络使用路由器。

- 你的网络已连接到 Internet，无 NAT 或代理服务器。

除非已禁用与 DHCP 相关的消息，否则 DHCP 消息会在 DHCP 寻址和自动专用 IP 寻址之间进行更改时向你提供通知。 如果意外禁用了 DHCP 消息传递，则可以通过将以下注册表项中的 PopupFlag 值的值从00改为01来重新启用 DHCP 消息：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\DHCP`

请注意，必须重新启动计算机才能使更改生效。 你还可以使用 Windows Millennium Edition、Windows 98 或 Windows 98 Second 版中的 Winipcfg 工具来确定你的计算机是否在使用 APIPA：

单击 "开始"，再单击 "运行"，键入 "winipcfg" （不带引号），然后单击 "确定"。 单击 "详细信息"。 如果 IP 自动配置地址框包含 169.254. 范围内的 IP 地址，则会启用自动专用 IP 寻址。 如果 "IP 地址" 框存在，则当前未启用自动专用 IP 寻址。
对于 Windows 2000、Windows XP 或 Windows Server 2003，你可以在命令提示符处使用 IPconfig 命令确定你的计算机是否在使用 APIPA：

单击 "开始"，再单击 "运行"，键入 "cmd" （不带引号），然后单击 "确定" 以打开 MS-DOS 命令行窗口。 键入 "ipconfig/all" （不带引号），然后按 ENTER 键。 如果启用了 "自动配置" 行显示 "是"，并且 "自动配置 IP 地址" 为 169.254. （其中，x 是客户端的唯一标识符），则计算机将使用 APIPA。 如果 "已启用自动配置" 行显示 "否"，则表示计算机当前未使用 APIPA。
可以通过使用以下方法之一来禁用自动专用 IP 寻址。

你可以手动配置 TCP/IP 信息，这将完全禁用 DHCP。 可以通过编辑注册表来禁用自动专用 IP 寻址（而非 DHCP）。 为此，可以将值为0x0 的 "IPAutoconfigurationEnabled" DWORD 注册表项添加到 Windows Millennium Edition、Windows98 或 Windows 98 Second Edition 的以下注册表项：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\VxD\DHCP`

对于 Windows 2000、Windows XP 和 Windows Server 2003，可以通过将值为0x0 的 "IPAutoconfigurationEnabled" DWORD 注册表项添加到以下注册表项来禁用 APIPA：`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters\Interfaces\<Adapter GUID>`
> [!NOTE]
> **适配器 GUID**子项是计算机 LAN 适配器的全局唯一标识符（GUID）。

将 IPAutoconfigurationEnabled DWORD 条目的值指定为1将启用 APIPA，这是从注册表中省略此值时的默认状态。

## <a name="examples-of-where-apipa-may-be-useful"></a>APIPA 可能有用的示例

### <a name="example-1-no-previous-ip-address-and-no-dhcp-server"></a>示例1：没有以前的 IP 地址，也没有 DHCP 服务器

如果基于 Windows 的计算机（配置为 DHCP）正在初始化，则会广播三个或更多 "发现" 消息。 如果 DHCP 服务器在广播多个发现消息后没有响应，则 Windows 计算机会为自身分配一个类 B （APIPA）地址。 然后，Windows 计算机将向计算机的用户显示一条错误消息（以前从未向它分配 DHCP 服务器的 IP 地址）。 Windows 计算机每隔三分钟发送一次发现消息，尝试建立与 DHCP 服务器的通信。

### <a name="example-2-previous-ip-address-and-no-dhcp-server"></a>示例2：以前的 IP 地址，没有 DHCP 服务器

计算机检查 DHCP 服务器，如果找不到，则尝试联系默认网关。 如果默认网关应答，则 Windows 计算机将保留以前租用的 IP 地址。 但是，如果计算机没有收到来自默认网关的响应，或者未分配任何响应，则它将使用自动专用 IP 寻址功能为自己分配 IP 地址。 将向用户显示一条错误消息，并每隔3分钟传输一次发现消息。 DHCP 服务器进入行后，会生成一条消息，指出已与 DHCP 服务器重新建立通信。

### <a name="example-3-lease-expires-and-no-dhcp-server"></a>示例3：租约过期且无 DHCP 服务器

基于 Windows 的计算机尝试重新建立 IP 地址的租约。 如果 Windows 计算机没有找到 DCHP 服务器，则会在生成错误消息之后为自己分配 IP 地址。 然后，计算机将广播四个发现消息，每5分钟一次，它会重复整个过程，直到 DHCP 服务器联机。 随后会生成一条消息，指出已与 DHCP 服务器重新建立通信。
