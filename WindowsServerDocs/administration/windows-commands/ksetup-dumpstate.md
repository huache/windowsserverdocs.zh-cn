---
title: ksetup： dumpstate
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46f827d26d867392db4cbef92cf5be496aee8d74
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841510"
---
# <a name="ksetupdumpstate"></a>ksetup： dumpstate



显示计算机上定义的所有领域的领域设置的当前状态。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /dumpstate
```

#### <a name="parameters"></a>参数

无

## <a name="remarks"></a>备注

此命令的输出包括默认领域（计算机所属的域）和在此计算机上定义的所有领域。 每个领域包含以下各项：
-   与此领域关联的所有密钥分发中心（Kdc）
-   此领域的所有**集领域**标志
-   KDC 密码

此命令不会显示 DNS 检测或命令**ksetup/domain**指定的域名。

此命令不显示使用命令**ksetup/setcomputerpassword**设置的计算机密码。

**Ksetup**生成与**Ksetup/dumpstate**相同的输出。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

查找计算机上的大多数 Kerberos 领域配置：
```
ksetup /dumpstate
```

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)