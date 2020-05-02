---
title: manage-bde autounlock
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 063528bf-d235-4b44-887a-52a7d983e01a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1cc467c4afcfa2df344e9190a341a9aad086c1ea
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724217"
---
# <a name="manage-bde-autounlock"></a>manage-bde： autounlock



管理受 BitLocker 保护的数据驱动器的自动解锁。

## <a name="syntax"></a>语法

```
manage-bde -autounlock [{-enable|-disable|-clearallkeys}] <Drive> [-computername <Name>] [{-?|/?}] [{-help|-h}]

```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|-enable|启用数据驱动器自动解锁。|
|-disable|禁用数据驱动器自动解锁。|
|-clearallkeys|删除操作系统驱动器上的所有存储的外部密钥。|
|\<驱动器>|表示驱动器号后跟一个冒号。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

为了说明如何使用 **-autounlock**命令启用数据驱动器 E 的自动解锁。
```
manage-bde –autounlock -enable E:
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)