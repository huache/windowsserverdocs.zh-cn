---
title: whoami
description: Whoami 的参考文章，其中显示了当前登录到本地系统的用户的用户、组和特权信息。
ms.topic: reference
ms.assetid: 6e3f4d5c-f1f5-4429-b602-afad2b3488bf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: baeb3781cb35f7066224dc19e9ce3ae4edf714ec
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641216"
---
# <a name="whoami"></a>whoami



显示当前登录到本地系统的用户的用户、组和特权信息。 如果在没有参数的情况下使用，则 **whoami** 将显示当前的域和用户名。



## <a name="syntax"></a>语法

```
whoami [/upn | /fqdn | /logonid]
whoami {[/user] [/groups] [/priv]} [/fo <Format>] [/nh]
whoami /all [/fo <Format>] [/nh]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/upn| (UPN) 格式显示用户主体名称中的用户名。|
|/fqdn|显示 (FQDN) 格式的完全限定域名中的用户名。|
|/logonid|显示当前用户的登录 ID。|
|/user|显示 (SID) 的当前域和用户名以及安全标识符。|
|/groups|显示当前用户所属的用户组。|
|/priv|显示当前用户的安全权限。|
|/fo \<Format>|指定输出格式。 有效值包括：</br>**表** 显示表中的输出。 这是默认值。</br>**列表** 在列表中显示输出。</br>**csv** 以逗号分隔的值（ (CSV) 格式显示输出。|
|/all|显示当前访问令牌中的所有信息，包括当前用户名、安全标识符 (当前用户所属的 SID) 、特权和组。|
|/nh|指定列标题不应显示在输出中。 这仅对表和 CSV 格式有效。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要显示当前登录到此计算机的用户的域和用户名，请键入：
```
whoami
```
将显示类似于下面的输出：
```
DOMAIN1\administrator
```
若要显示当前访问令牌中的所有信息，请键入：
```
whoami /all
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)