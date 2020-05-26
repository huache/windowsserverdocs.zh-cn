---
title: manage-bde forcerecovery
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eecae37c-c9a3-46c5-b615-a0ace1f1d778
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1213eb583099a575fd118b1ade5d2c9b82c6dea7
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820677"
---
# <a name="manage-bde-forcerecovery"></a>manage-bde： forcerecovery



重新启动时，强制 BitLocker 保护的驱动器进入恢复模式。 此命令删除驱动器中与受信任的平台模块（TPM）相关的密钥保护程序。 计算机重新启动时，只能使用恢复密码或恢复密钥来解锁驱动器。

## <a name="syntax"></a>语法

```
manage-bde –forcerecovery <Drive> [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<驱动器>|表示驱动器号后跟一个冒号。|
|-computername|指定 Manage-bde.exe 将用于修改另一台计算机上的 BitLocker 保护。 你还可以使用 **-cn**作为此命令的缩写形式。|
|\<Name>|表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。|
|-? 或 /?|在命令提示符下显示 brief Help。|
|-help 或-h|在命令提示符下显示完整的帮助。|

## <a name="examples"></a>示例

为了说明如何使用 **-forcerecovery**命令来使 BitLocker 在驱动器 C 上以恢复模式启动。
```
manage-bde –forcerecovery C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Manage-bde](manage-bde.md)