---
title: manage-bde tpm
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 11a8530d-edd7-4fe3-ae81-b943766760fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b6495bfbfedea7219ae175145f72fc12314ce7ae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839760"
---
# <a name="manage-bde-tpm"></a>manage-bde： tpm

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012
> 
> [!IMPORTANT]
> 此命令不支持在运行 Windows 8、Windows Server 2012 或更高版本操作系统的计算机上使用。 对于这些计算机，你可以使用[适用于 Windows PowerShell 的 TPM 管理 cmdlet](https://docs.microsoft.com/powershell/module/trustedplatformmodule/)。
> 如果在运行 Windows 7 或 Windows Server 2008 的计算机上使用此命令，则仍可使用此命令配置计算机的受信任的平台模块（TPM）。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。
> ## <a name="syntax"></a>语法
> ```
> manage-bde -tpm [-turnon] [-takeownership <OwnerPassword>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
> ```
> #### <a name="parameters"></a>参数
> 
> |    参数    |                                                                              说明                                                                               |
> |-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |     -turnon     |              启用和激活 TPM，允许设置 TPM 所有者密码。 你还可以使用 **-t**作为此命令的缩写形式。              |
> | -takeownership  |                      通过设置所有者密码来取得 TPM 的所有权。 你还可以使用 **-o**作为此命令的缩写形式。                       |
> | <OwnerPassword> |                                                      表示你为 TPM 指定的所有者密码。                                                       |
> |  -computername  | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
> |     <Name>      |    表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。     |
> |    -? 或 /?     |                                                               在命令提示符下显示 brief help。                                                               |
> |   -help 或-h   |                                                             在命令提示符下显示完整的帮助。                                                              |
> 
> ## <a name="examples"></a><a name=BKMK_Examples></a>示例
> 下面的示例演示如何使用 **-tpm**命令打开 tpm。
> ```
> manage-bde  tpm -turnon
> ```
> 下面的示例演示如何使用**tpm**命令获取 tpm 的所有权，并将所有者密码设置为 0wnerP@ss。
> ```
> manage-bde  tpm  takeownership 0wnerP@ss
> ```
> ## <a name="additional-references"></a>其他参考
> -   - [命令行语法项](command-line-syntax-key.md)
> -   [manage-bde](manage-bde.md)
