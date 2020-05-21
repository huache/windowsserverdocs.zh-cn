---
title: fsutil tiering
description: Fsutil tiering 命令的参考主题，可用于管理存储层功能，如设置和禁用层标志和列表。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: e5f55f3e-8d2a-4526-8d67-36a539126c22
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 6fa8646dcdf7e836ccb45f253e0c4f8691b1ea3c
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436842"
---
# <a name="fsutil-tiering"></a>fsutil tiering

> 适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows 10

启用存储层功能的管理，例如设置和禁用层标志和列表。

## <a name="syntax"></a>语法

```
fsutil tiering [clearflags] <volume> <flags>
fsutil tiering [queryflags] <volume>
fsutil tiering [regionlist] <volume>
fsutil tiering [setflags] <volume> <flags>
fsutil tiering [tierlist] <volume>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| clearflags | 禁用卷的分层行为标志。 |
| `<volume>` | 指定卷。 |
| /trnh | 对于具有分层存储的卷，会使热收集处于禁用状态。<p>仅适用于 NTFS 和 ReFS。 |
| queryflags | 查询卷的分层行为标志。 |
| regionlist | 列出卷的分层区域及其各自的存储层。 |
| setflags | 启用卷的分层行为标志。 |
| tierlist | 列出与卷关联的存储层。 |

### <a name="examples"></a>示例

若要查询卷 C 上的标志，请键入：

```
fsutil tiering clearflags C:
```

若要设置卷 C 上的标志，请键入：

```
fsutil tiering setflags C: /trnh
```

若要清除卷 C 上的标志，请键入：

```
fsutil tiering clearflags C: /trnh
```

若要列出第 C 个区域及其各自的存储层，请键入：

```
fsutil tiering regionlist C:
```

若要列出卷 C 的层，请键入：

```
fsutil tiering tierlist C:
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
