---
title: bitsadmin getproxybypasslist
description: Bitsadmin getproxybypasslist 命令的参考文章，它检索指定作业的代理跳过列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 67e6e4a54bb8c4929acbbaa47c78e33bab95a283
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926836"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

检索指定作业的代理跳过列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxybypasslist <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>备注

旁路列表包含不是通过代理路由的主机名或 IP 地址。 此列表可以包含 `<local>` 以引用同一 LAN 上的所有服务器。 列表可以为分号（;)或以空格分隔。

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的代理跳过列表：

```
bitsadmin /getproxybypasslist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
