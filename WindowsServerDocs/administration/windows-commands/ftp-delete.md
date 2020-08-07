---
title: ftp delete
description: Ftp delete 命令的参考文章，用于删除远程计算机上的文件。
ms.topic: article
ms.assetid: 067c45f3-e4e8-4450-b8b6-836994f6adfe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 315a73f0ebfbefdf4a7033f42c2cad02e2ab77bc
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87889522"
---
# <a name="ftp-delete"></a>ftp delete

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除远程计算机上的文件。

## <a name="syntax"></a>语法

```
delete <remotefile>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<remotefile>` | 指定要删除的文件。 |

### <a name="examples"></a>示例

若要删除远程计算机上的*test.txt*文件，请键入：

```
delete test.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
