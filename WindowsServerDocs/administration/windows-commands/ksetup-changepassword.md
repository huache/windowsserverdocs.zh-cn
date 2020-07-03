---
title: ksetup changepassword
description: Ksetup changepassword 命令的参考文章，此命令使用密钥发行中心（KDC）密码（kpasswd）值更改登录用户的密码。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 283078e7-a88f-4875-90e6-f8605e6b7ea7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e49a9c0a796357c89efd3c86373c77468670176c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925503"
---
# <a name="ksetup-changepassword"></a>ksetup changepassword

使用密钥发行中心（KDC）密码（kpasswd）值更改登录用户的密码。 命令的输出会通知你成功或失败状态。

可以通过运行**kpasswd** `ksetup /dumpstate` 命令并查看输出来检查是否已设置 kpasswd。


## <a name="syntax"></a>语法

```
ksetup /changepassword <oldpassword> <newpassword>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<oldpassword>` | 指定已登录用户的现有密码。 |
| `<newpassword>` | 指定已登录用户的新密码。 此密码必须满足在此计算机上设置的所有密码要求。 |

#### <a name="remarks"></a>备注

- 如果在当前域中找不到用户帐户，系统将要求你提供用户帐户所在的域名。

- 如果要在下次登录时强制更改密码，则此命令允许使用星号（*），因此系统将提示用户输入新密码。

-

### <a name="examples"></a>示例

若要更改当前登录到此计算机的用户的密码，请键入：

```
ksetup /changepassword Pas$w0rd Pa$$w0rd
```

若要更改当前登录到 Contoso 域的用户的密码，请键入：

```
ksetup /domain CONTOSO /changepassword Pas$w0rd Pa$$w0rd
```

若要强制当前登录的用户在下次登录时更改密码，请键入：

```
ksetup /changepassword Pas$w0rd *
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup dumpstate 命令](ksetup-dumpstate.md)

- [ksetup addkpasswd 命令](ksetup-addkpasswd.md)

- [ksetup delkpasswd 命令](ksetup-delkpasswd.md)

- [ksetup dumpstate 命令](ksetup-dumpstate.md)
