---
title: ksetup dumpstate
description: Ksetup dumpstate 命令的参考主题，该主题显示计算机上定义的所有领域的领域设置的当前状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ccb75ac143239d97b823fb7030f9a8020b4b4f6
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817737"
---
# <a name="ksetup-dumpstate"></a>ksetup dumpstate

显示计算机上定义的所有领域的领域设置的当前状态。 此命令显示与**ksetup**命令相同的输出。

## <a name="syntax"></a>语法

```
ksetup /dumpstate
```

### <a name="remarks"></a>备注

- 此命令的输出包括默认领域（计算机所属的域）和在此计算机上定义的所有领域。 每个领域包含以下各项：

  - 与此领域关联的所有密钥分发中心（Kdc）。

  - 此领域的所有**集领域**标志。

  - KDC 密码。

- 此命令不会显示 DNS 检测或命令指定的域名 `ksetup /domain` 。

- 此命令不显示使用命令设置的计算机密码 `ksetup /setcomputerpassword` 。

## <a name="examples"></a>示例

若要在计算机上查找 Kerberos 领域配置，请键入：

```
ksetup /dumpstate
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)