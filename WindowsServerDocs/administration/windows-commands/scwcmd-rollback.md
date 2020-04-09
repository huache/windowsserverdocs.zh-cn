---
title: Scwcmd 回滚
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9679f8a8ef2e62f451d7ee01c3c5718825b5cbeb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835140"
---
# <a name="scwcmd-rollback"></a>Scwcmd: rollback

> 适用于：Windows Server 2012 R2、Windows Server 2012

应用最新的可用回滚策略，然后删除该回滚策略。

## <a name="syntax"></a>语法

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/m：\<ComputerName >|指定应在其中执行回滚操作的计算机的 NetBIOS 名称、DNS 名称或 IP 地址。|
|/u：\<用户名 >|指定执行远程回滚时要使用的备用用户帐户。 默认值为已登录的用户。|
|/pw：\<密码 >|指定执行远程回滚时要使用的备用用户凭据。 默认值为已登录的用户。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

若要在 IP 地址172.16.0.0 中回滚计算机上的安全策略，请键入：
```
scwcmd rollback /m:172.16.0.0
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)