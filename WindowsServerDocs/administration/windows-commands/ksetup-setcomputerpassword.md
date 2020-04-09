---
title: ksetup： setcomputerpassword
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e65ea6e935d9fde9c23842755c36e418928dec7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841370"
---
# <a name="ksetupsetcomputerpassword"></a>ksetup： setcomputerpassword



设置本地计算机的密码。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /setcomputerpassword <Password>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<密码 >|使用提供的密码设置本地计算机上的计算机帐户。</br>只能使用具有管理权限的帐户来设置密码。 密码长度可以是1到156个字母数字或特殊字符。|

## <a name="remarks"></a>备注

此命令仅影响计算机帐户。

您必须重新启动计算机才能使密码更改生效。

计算机帐户密码不会在注册表中显示，也不会显示为**ksetup**命令的输出。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

将本地计算机上的计算机帐户密码从 IPops897 更改为 IPop $ 897！。
```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)