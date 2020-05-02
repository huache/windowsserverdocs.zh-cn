---
title: ksetup： setcomputerpassword
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cb0c2ee36ed85ddfb015a80e86198fe788f8474
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724583"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup： setcomputerpassword



设置本地计算机的密码。

## <a name="syntax"></a>语法

```
ksetup /setcomputerpassword <Password>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<密码>|使用提供的密码设置本地计算机上的计算机帐户。</br>只能使用具有管理权限的帐户来设置密码。 密码长度可以是1到156个字母数字或特殊字符。|

## <a name="remarks"></a>备注

此命令仅影响计算机帐户。

您必须重新启动计算机才能使密码更改生效。

计算机帐户密码不会在注册表中显示，也不会显示为**ksetup**命令的输出。

## <a name="examples"></a>示例

将本地计算机上的计算机帐户密码从 IPops897 更改为 IPop $ 897！。
```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)