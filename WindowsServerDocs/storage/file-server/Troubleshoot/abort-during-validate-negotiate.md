---
title: 验证协商期间 TCP 连接中止
description: 介绍如何解决在验证协商期间 TCP 连接中止的 SMB 问题。
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 36bd49777899870246a19531c6681a5b45bb622d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815510"
---
# <a name="tcp-connection-is-aborted-during-validate-negotiate"></a>验证协商期间 TCP 连接中止

在 SMB 问题的网络跟踪中，你会注意到在验证协商过程中发生了 TCP 重置中止。 本文介绍如何解决此问题。

## <a name="cause"></a>原因

此问题可能是由于协商验证失败引起的。 出现这种情况通常是因为 WAN 加速器修改了原始 SMB 协商数据包。

由于任何原因，Microsoft 不再允许修改验证协商数据包。 这是因为此行为会造成严重的安全风险。

以下要求适用于验证协商数据包：

- 验证协商过程使用 FSCTL\_验证\_NEGOTIATE\_INFO 命令。

- 验证协商响应必须经过签名。 否则，连接将中止。

- 应比较 FSCTL\_验证\_将\_信息消息协商到 Negotiate 消息，以确保未更改任何内容。

## <a name="workaround"></a>解决方法

你可以暂时禁用验证协商过程。 为此，请找到以下注册表子项：

**HKEY\_本地\_计算机\\SYSTEM\\CurrentControlSet\\Services\\LanmanWorkstation\\参数**

在**Parameters**项下，将**RequireSecureNegotiate**设置为**0**。

在 Windows PowerShell 中，可以运行以下命令来设置此值：

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters" RequireSecureNegotiate -Value 0 -Force
```

> [!NOTE]
> 无法在 windows 10、Windows Server 2016 或更高版本的 Windows 中禁用验证协商过程。

如果客户端或服务器无法支持 "验证协商" 命令，则可以通过将 SMB 签名设置为 "必需" 来解决此问题。 SMB 签名比验证协商更安全。 但是，如果需要签名，也可能会降低性能。

## <a name="reference"></a>参考

有关详细信息，请参阅以下文章：

[3.3.5.15.12 处理验证协商信息请求](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/0b7803eb-d561-48a4-8654-327803f59ec6)

[3.2.5.14.12 处理验证协商信息响应](https://docs.microsoft.com/openspecs/windows_protocols/ms-smb2/6a5bc90d-3c08-4498-905b-e7dab30b2e0e)
