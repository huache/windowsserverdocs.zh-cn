---
title: fsutil transaction
description: 用于管理 NTFS 事务的 "fsutil transaction" 命令的参考文章。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: f2eefaaf-2817-4ac7-abac-d2b65fa971dc
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: f70281af6ecf652cc1dba95ec09b07529f71752e
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87889794"
---
# <a name="fsutil-transaction"></a>fsutil transaction

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

管理 NTFS 事务。

## <a name="syntax"></a>语法

```
fsutil transaction [commit] <GUID>
fsutil transaction [fileinfo] <filename>
fsutil transaction [list]
fsutil transaction [query] [{files | all}] <GUID>
fsutil transaction [rollback] <GUID>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 提交 (commit) | 标记成功的隐式或显式指定的事务的结束。 |
| `<GUID>` | 指定表示事务的 GUID 值。 |
| fileinfo  | 显示指定文件的事务信息。 |
| `<filename>` | 指定完整路径和文件名。 |
| list | 显示当前正在运行的事务的列表。 |
| query | 显示指定事务的信息。<ul><li>如果 `fsutil transaction query files` 指定了，则仅为指定的事务显示文件信息。</li><li>如果 `fsutil transaction query all` 指定了，则将显示该事务的所有信息。</li></ul> |
| 回滚 | 将指定的事务回滚到开始处。 |

### <a name="examples"></a>示例

若要显示文件*c:\test.txt*的事务信息，请键入：

```
fsutil transaction fileinfo c:\test.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [事务性 NTFS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730726(v=ws.10))
