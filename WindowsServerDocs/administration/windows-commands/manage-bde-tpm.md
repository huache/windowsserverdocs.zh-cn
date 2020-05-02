---
title: manage-bde tpm
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 11a8530d-edd7-4fe3-ae81-b943766760fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afb3859a1795959c90e71391b2926164165ef9ce
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724075"
---
# <a name="manage-bde-tpm"></a>manage-bde： tpm

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012
> 
> [!IMPORTANT]
> 此命令不支持在运行 Windows 8、Windows Server 2012 或更高版本操作系统的计算机上使用。 对于这些计算机，你可以使用[适用于 Windows PowerShell 的 TPM 管理 cmdlet](https://docs.microsoft.com/powershell/module/trustedplatformmodule/)。
> 如果在运行 Windows 7 或 Windows Server 2008 的计算机上使用此命令，则仍可使用此命令配置计算机的受信任的平台模块（TPM）。
> ## <a name="syntax"></a>语法
> ```
> manage-bde -tpm [-turnon] [-takeownership <OwnerPassword>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
> ```
> #### <a name="parameters"></a>参数
> 
> |    参数    |                                                                              描述                                                                               |
> |-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |     -turnon     |              启用和激活 TPM，允许设置 TPM 所有者密码。 你还可以使用 **-t**作为此命令的缩写形式。              |
> | -takeownership  |                      通过设置所有者密码来取得 TPM 的所有权。 你还可以使用 **-o**作为此命令的缩写形式。                       |
> | <OwnerPassword> |                                                      表示你为 TPM 指定的所有者密码。                                                       |
> |  -computername  | 指定 manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。 |
> |     <Name>      |    表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。     |
> |    -? 或 /?     |                                                               在命令提示符下显示 brief help。                                                               |
> |   -help 或-h   |                                                             在命令提示符下显示完整的帮助。                                                              |
> 
> ## <a name="examples"></a>示例
> 说明如何使用 **-tpm**命令打开 tpm。
> ```
> manage-bde  tpm -turnon
> ```
> 为了说明如何使用**tpm**命令获取 tpm 的所有权，并将所有者密码设置为0wnerP@ss。
> ```
> manage-bde  tpm  takeownership 0wnerP@ss
> ```
> ## <a name="additional-references"></a>其他参考
> -   - [命令行语法项](command-line-syntax-key.md)
> -   [manage-bde](manage-bde.md)
