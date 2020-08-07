---
title: Scwcmd 回滚
description: '* * * * 的参考文章'
ms.topic: article
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e0fc158584c15c021b14c96829fe0266c3193be
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883125"
---
# <a name="scwcmd-rollback"></a>Scwcmd: rollback

> 适用于： Windows Server 2012 R2、Windows Server 2012

应用最新的可用回滚策略，然后删除该回滚策略。

## <a name="syntax"></a>语法

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|一样\<ComputerName>|指定应在其中执行回滚操作的计算机的 NetBIOS 名称、DNS 名称或 IP 地址。|
|/u\<UserName>|指定执行远程回滚时要使用的备用用户帐户。 默认值为已登录的用户。|
|pw\<Password>|指定执行远程回滚时要使用的备用用户凭据。 默认值为已登录的用户。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd.exe 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a>示例

若要在 IP 地址172.16.0.0 中回滚计算机上的安全策略，请键入：
```
scwcmd rollback /m:172.16.0.0
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)