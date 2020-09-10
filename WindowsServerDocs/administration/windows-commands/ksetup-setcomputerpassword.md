---
title: ksetup setcomputerpassword
description: Ksetup setcomputerpassword 命令的参考文章，用于设置本地计算机的密码。
ms.topic: reference
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9bd9d9fafae57c1c7804f7a214d9729cdb232b2d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627433"
---
# <a name="ksetup-setcomputerpassword"></a>ksetup setcomputerpassword

设置本地计算机的密码。 此命令仅影响计算机帐户，需要重新启动才能使密码更改生效。

> [!IMPORTANT]
> 计算机帐户密码不会在注册表中显示，也不会显示为 **ksetup** 命令的输出。

## <a name="syntax"></a>语法

```
ksetup /setcomputerpassword <password>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<password>` | 指定提供的密码以设置本地计算机上的计算机帐户。 只能使用具有管理权限的帐户来设置密码，并且密码必须为1到156个字母数字或特殊字符。 |

### <a name="examples"></a>示例

若要将本地计算机上的计算机帐户密码从 *IPops897* 更改为 *IPop $ 897！*，请键入：

```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)
