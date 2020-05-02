---
title: ksetup： changepassword
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 283078e7-a88f-4875-90e6-f8605e6b7ea7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32c48e896b77043820eea42159e20c089bd69fb8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724727"
---
# <a name="ksetupchangepassword"></a>ksetup： changepassword



使用密钥发行中心（KDC）密码（kpasswd）值更改登录用户的密码。

## <a name="syntax"></a>语法

```
ksetup /changepassword <OldPasswd> <NewPasswd>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<OldPasswd>|指出登录用户的现有密码。|
|\<NewPasswd>|指出登录用户的新密码。|

## <a name="remarks"></a>备注

此命令使用 KDC 密码（kpasswd）值更改登录用户的密码。 通过运行**ksetup/dumpstate**命令，kpasswd （如果已设置）显示在输出中。

用户的新密码必须满足在此计算机上设置的所有密码要求。

如果在当前域中找不到用户帐户，系统将要求你提供用户帐户所在的域名。

如果要在下次登录时强制更改密码，则此命令允许使用星号（*），因此系统将提示用户输入新密码。

命令的输出会通知你成功或失败状态。

## <a name="examples"></a>示例

更改此域中当前登录到此计算机的用户的密码：
```
ksetup /changepassword Pas$w0rd Pa$$w0rd
```
更改在 Contoso 域中当前登录的用户的密码：
```
ksetup /domain CONTOSO /changepassword Pas$w0rd Pa$$w0rd
```
强制当前登录的用户在下次登录时更改密码：
```
ksetup /changepassword Pas$w0rd *
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)