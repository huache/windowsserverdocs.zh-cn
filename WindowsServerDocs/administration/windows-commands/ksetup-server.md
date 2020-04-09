---
title: ksetup：服务器
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7889e1a03d3c0eec1958bf1d6356c67e9371a80f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841440"
---
# <a name="ksetupserver"></a>ksetup：服务器



允许您为运行 Windows 操作系统的计算机指定一个名称，以便使用**ksetup**进行的更改将更新目标计算机。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /server <ServerName>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ServerName >|配置将对其有效的完整计算机名称，例如 IPops897.corp.contoso.com。</br>如果指定了不完整的完全限定的域计算机名称，则该命令将失败。|

## <a name="remarks"></a>备注

无法删除目标服务器名称;您只能将其更改回本地计算机名称，这是默认值。

目标服务器名称存储在注册表的**HKEY_LOCAL_MACHINE \system\controlset001\control\lsa\kerberos**中。 不能使用**ksetup**报告它。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

使**ksetup**配置在连接到 Contoso 域的 IPops897 计算机上生效：
```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)