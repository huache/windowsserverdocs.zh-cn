---
title: ftp user
description: Ftp 用户命令的参考文章，用于指定远程计算机的用户。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9b1eea449765b58461d410f0e015d4978c3ad016
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957349"
---
# <a name="ftp-user"></a>ftp user

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

指定远程计算机的用户。

## <a name="syntax"></a>语法

```
user <username> [<password>] [<account>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<username>` | 指定登录到远程计算机时使用的用户名。 |
| `[<password>]` | 指定*用户名*的密码。 如果未指定密码，但需要密码， **ftp**命令会提示输入密码。 |
| `[<account>]` | 指定用于登录到远程计算机的帐户。 如果未指定*帐户*，但需要， **ftp**命令会提示输入帐户。 |

### <a name="examples"></a>示例

若要指定具有密码*Password1*的*User1* ，请键入：

```
user User1 Password1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
