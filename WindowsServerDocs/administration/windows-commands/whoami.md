---
title: whoami
description: 适用于 whoami 的 Windows 命令主题，用于显示当前登录到本地系统的用户的用户、组和特权信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3f4d5c-f1f5-4429-b602-afad2b3488bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ff45ed95b35215859f2f83aec75b33570ef46d2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829270"
---
# <a name="whoami"></a>whoami



显示当前登录到本地系统的用户的用户、组和特权信息。 如果在没有参数的情况下使用，则**whoami**将显示当前的域和用户名。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
whoami [/upn | /fqdn | /logonid]
whoami {[/user] [/groups] [/priv]} [/fo <Format>] [/nh]
whoami /all [/fo <Format>] [/nh]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/upn|以用户主体名称（UPN）格式显示用户名。|
|/fqdn|显示采用完全限定的域名（FQDN）格式的用户名。|
|/logonid|显示当前用户的登录 ID。|
|/user|显示当前域和用户名以及安全标识符（SID）。|
|/groups|显示当前用户所属的用户组。|
|/priv|显示当前用户的安全权限。|
|/fo \<格式 >|指定输出格式。 有效值包括：</br>**表**显示表中的输出。 这是默认值。</br>**列表**在列表中显示输出。</br>**csv**以逗号分隔值（CSV）格式显示输出。|
|/all|显示当前访问令牌中的所有信息，包括当前用户名、安全标识符（SID）、权限以及当前用户所属的组。|
|/nh|指定列标题不应显示在输出中。 这仅对表和 CSV 格式有效。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要显示当前登录到此计算机的用户的域和用户名，请键入：
```
whoami
```
将显示类似于以下内容的输出：
```
DOMAIN1\administrator
```
若要显示当前访问令牌中的所有信息，请键入：
```
whoami /all
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)