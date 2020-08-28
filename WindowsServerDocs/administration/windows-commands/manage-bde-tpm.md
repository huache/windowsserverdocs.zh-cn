---
title: manage-bde tpm
description: Manage-bde tpm 命令的参考文章，它配置计算机的受信任的平台模块 (TPM) 。
ms.topic: reference
ms.assetid: 11a8530d-edd7-4fe3-ae81-b943766760fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1aa9653b77a72c90449234e39891fa457deca82d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033965"
---
# <a name="manage-bde-tpm"></a>manage-bde tpm

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

 (TPM) 配置计算机的受信任的平台模块。

## <a name="syntax"></a>语法

```
manage-bde -tpm [-turnon] [-takeownership <ownerpassword>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| -turnon | 启用和激活 TPM，允许设置 TPM 所有者密码。 你还可以使用 **-t** 作为此命令的缩写形式。 |
| -takeownership | 通过设置所有者密码来取得 TPM 的所有权。 你还可以使用 **-o** 作为此命令的缩写形式。 |
| `<ownerpassword>` | 表示你为 TPM 指定的所有者密码。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要启用 TPM，请键入：

```
manage-bde  tpm -turnon
```

若要获取 TPM 的所有权并将所有者密码设置为 *0wnerP@ss* ，请键入：

```
manage-bde  tpm  takeownership 0wnerP@ss
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [适用于 Windows PowerShell 的 TPM 管理 cmdlet](/powershell/module/trustedplatformmodule/)

- [manage-bde 命令](manage-bde.md)
