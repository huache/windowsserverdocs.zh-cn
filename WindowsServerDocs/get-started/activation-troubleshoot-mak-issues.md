---
title: MAK 激活已知问题
description: 描述在 MAK 激活过程中可能发生的常见问题，并提供解决方法和指南
ms.topic: article
ms.date: 10/3/2019
ms.technology: server-general
author: Teresa-Motiv
ms.author: v-tea
manager: dcscontentpm
ms.localizationpriority: medium
ms.openlocfilehash: 0f4153387d740379e66eca9e8069b7a446a1ec71
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80826230"
---
# <a name="mak-activation-known-issues"></a>MAK 激活：已知问题

本文描述在多次激活密钥 (MAK) 激活期间可能发生的常见问题，并提供解决这些问题的指南。

## <a name="how-can-i-tell-whether-my-computer-is-activated"></a>我如何判断我的计算机是否已激活？

在计算机上，打开“系统”控制面板并查找“Windows 已激活”   。 或者，运行 Slmgr.vbs 并使用 /dli 命令行选项  。

## <a name="the-computer-does-not-activate-over-the-internet"></a>计算机不能通过 Internet 激活

请确保在防火墙中打开必需的端口。 要获取端口列表，请参阅[批量激活部署指南](https://go.microsoft.com/fwlink/?linkid=150083)。

## <a name="internet-and-telephone-activation-fail"></a>Internet 和电话激活失败

请联系当地的 Microsoft 激活中心。 有关全球 Microsoft 激活中心的电话号码，请转到[全球 Microsoft 许可激活中心电话号码](https://www.microsoft.com/Licensing/existing-customer/activation-centers)。 拨打电话时，请务必提供批量许可协议信息和购买证明。

## <a name="slmgrvbs-ato-returns-an-error-code"></a>Slmgr.vbs /ato 将返回错误代码

如果 Slmgr.vbs 返回十六进制错误代码，请通过运行以下脚本确定相应的错误消息：

```cmd
slui.exe 0x2a 0x <ErrorCode>
```

有关具体错误代码以及如何解决它们的详细信息，请参阅[解决常见激活错误代码](activation-error-codes.md)。
