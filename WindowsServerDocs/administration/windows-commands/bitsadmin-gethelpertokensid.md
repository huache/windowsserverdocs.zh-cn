---
title: bitsadmin gethelpertokensid
description: Bitsadmin gethelpertokensid 命令的参考文章，返回 BITS 传输作业的帮助程序令牌的 SID （如果已设置）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: b616b9cc80b21c4c6a72fcca55dcdd893fac2730
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928195"
---
# <a name="bitsadmin-gethelpertokensid"></a>bitsadmin gethelpertokensid

返回 BITS 传输作业的 [帮助程序令牌](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)的 SID （如果已设置）。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokensid <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的 BITS 传输作业的 SID：

```
bitsadmin /gethelpertokensid myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
