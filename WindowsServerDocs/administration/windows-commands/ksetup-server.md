---
title: ksetup：服务器
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 91549eb78f825264016ec0e03b7035f79132f260
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724596"
---
# <a name="ksetupserver"></a>ksetup：服务器



允许您为运行 Windows 操作系统的计算机指定一个名称，以便使用**ksetup**进行的更改将更新目标计算机。

## <a name="syntax"></a>语法

```
ksetup /server <ServerName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<ServerName>|配置将对其有效的完整计算机名称，例如 IPops897.corp.contoso.com。</br>如果指定了不完整的完全限定的域计算机名称，则该命令将失败。|

## <a name="remarks"></a>备注

无法删除目标服务器名称;您只能将其更改回本地计算机名称，这是默认值。

目标服务器名称存储在注册表的**HKEY_LOCAL_MACHINE \system\controlset001\control\lsa\kerberos**中。 不能使用**ksetup**报告它。

## <a name="examples"></a>示例

使**ksetup**配置在连接到 Contoso 域的 IPops897 计算机上生效：
```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)